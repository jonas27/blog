---
title: "WebHooks in K8s"
date: 2020-04-04T08:53:24+01:00
draft: true
categories: ["k8s"]
tags: ["webhook"]
---
# Webhooks
AdmissionWebhooks in K8s are used to automatically mutate and validate resources. In this article I am going to focus on things I struggled with during my implementation of WebHooks.

## Certificates
Certficates can be a huge hassle and everyone who has ever worked with them can attest to it. What more, there is no way I found to debug webhooks. Is the webhook trying to make a call, but the url is wrong, the certificate is not valid or is the configuration wrong in the first place? It is weird that noone sofar has made them more transparant.

As so often in Kubernetes, we are dealing with mTLS, i.e. both parties trust each other before communicating any other information. This means the client not only calls the server but also demands its certificate and public key. The client then validates the certificate with the public key and checks whether it contains the correct *Subject* and *Issuer*.
However, on the server we can choose to ignore unknown certifcate authorities.

## Install Cert-Manager
This should not be too much of a problem, just follow their [install instructions](https://cert-manager.io/docs/installation/kubernetes/).

## Creating the Certificates
To produce the certificates I used openssl and cert-manager. First let's produce the singing key and root CA, for reference see [here](https://docs.cert-manager.io/en/release-0.9/tasks/issuers/setup-ca.html)

```
export COMMON_NAME = "webhook.webhook.svc"
openssl genrsa -out ca.key 2048
openssl req -x509 -new -nodes -key ca.key -subj "/CN=${COMMON_NAME}" -days 3650 -reqexts v3_req -extensions v3_ca -out ca.crt
```

Then, create a secret in kubernetes with the signing key and root CA. 

```
kubectl create secret tls ca-key-pair \
   --cert=ca.crt \
   --key=ca.key \
   --namespace=webhook
```

Next, we need to create a Issuer or ClusterIssuer which can make certificates based on the secret we just created.

```
<<EOF | kubectl apply -f -
apiVersion: cert-manager.io/v1alpha2
kind: Issuer
metadata:
  name: ca-issuer
  namespace: webhook
spec:
  ca:
    secretName: ca-key-pair
EOF
```

Finally, lets create a signed Certificate. 

```
<<EOF | kubectl apply -f -
apiVersion: cert-manager.io/v1alpha2
kind: Certificate
metadata:
  name: webhook-cert
  namespace: webhook
spec:
  # Secret names are always required.
  secretName: webhook-server-tls
  duration: 2160h # 90d
  renewBefore: 360h # 15d
  organization:
  - jetstack
  # The use of the common name field has been deprecated since 2000 and is
  # discouraged from being used.
  commonName: webhook.webhook.svc
  isCA: false
  keySize: 2048
  keyAlgorithm: rsa
  keyEncoding: pkcs1
  usages:
    - server auth
    - client auth
  # At least one of a DNS Name, USI SAN, or IP address is required.
  dnsNames:
  - webhook
  - webhook.webhook
  - webhook.webhook.svc
  - webhook.webhook.svc.cluster.loca
  uriSANs:
  - spiffe://cluster.local/ns/webhook/sa/webhook
  # ipAddresses:
  # - 192.168.0.5
  # Issuer references are always required.
  issuerRef:
    name: ca-issuer
    # We can reference ClusterIssuers by changing the kind here.
    # The default value is Issuer (i.e. a locally namespaced Issuer)
    kind: Issuer
    # This is optional since cert-manager will default to this value however
    # if you are using an external issuer, change this to that issuer group.
    group: cert-manager.io
EOF
```

You can make sure this works with:
```
kubectl describe certificate webhook-cert -n webhook
kubectl get secret webhook-server-tls -n webhook -o yaml
```

The second output also gives us the base64 encoded key and certificate. And thats it. We know created a certificate Issuer in cert-manager and let it issue a secret we can then use in the webhook server and client.

## Go Service
go-client

## ValidatingWebhook
We just generated the certificate but the webhook only accepts one base64 encoded CA so this means we need to decode the key and certificate, merge them and re-econde them both to base64. With a little of command line magic we can make this all on alone.
```
kubectl get secret webhook-server-tls -n webhook -o yaml | grep -m1 tls.crt | awk '{print $2}' | base64 --decode > webhook-client.pem
kubectl get secret webhook-server-tls -n webhook -o yaml | grep -m1 tls.crt | awk '{print $2}' | base64 --decode >> webhook-client.pem
base64 < webhook-client.pem > webhook-client64.pem
rm webhook-client.pem
```

Notice that this created a file called "webhook-client64.pem" in which the base64 encoded certificate is stored. We can then create the ValidationWebhook like so, where you fill in the caBundle with the contents of the just created file.

```
<<EOF | kubectl apply -f -
apiVersion: admissionregistration.k8s.io/v1
kind: ValidatingWebhookConfiguration
metadata:
  name: "webhook.webhook.svc"
webhooks:
- name: "webhook.webhook.svc"
  clientConfig:
    service:
      name: webhook
      namespace: webhook
      path: "/val"
      port: 443
    caBundle: <webhook-client64.pem>
  rules:
    - operations: ["CREATE"]
      apiGroups: [""]
      apiVersions: ["v1"]
      resources: ["pods"]
EOF
```