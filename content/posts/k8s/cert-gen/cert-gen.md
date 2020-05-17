---
title: "Cert-gen"
date: 2020-04-04T08:53:24+01:00
draft: true
image: "/posts/k8s/cert-gen/cert-gen-cover.png"
thumbnail: "/posts/k8s/cert-gen/cert-gen.png"
description: "cert-gen"
tldr: "cert-gen"
categories: ["k8s"]
classes: 
- feature-depth
- feature-figcaption
---
# cert-gen
Creating and managing your own certificates can be a lot of trouble. Kubernetes provides an in-build CA (certificate authority) for internal purposes, eg RBAC and other certificates. The root CA is created upon setting a cluster up via kubeadm. But certificates signed by the k8s CA are not trusted by your browser and so you end up something like this.

![hallo](/posts/k8s/cert-gen/cert_not_valid.png)

Your browser comes prepackaged with the public certificates from the most used CA to authenticated that the website is actually owned by the url you are trying to access. This is called trust and is strictly different from encryption. A website can provide certificates for communication, meaning it's traffic will be encrypted, but it can be not trusted by your browser (it is generally not pausbile in the web to have trust but no encryption). But with possible hundred different domains, how should you create and manage your certificates?


 [Cert-Manager](cert-manager.io) is solving this problem for Kubernetes. But, it does not provide a automatic way to create the certificates. Cert-gen is a cloud native service to fill this gab. It automatically creates certificate based on a few parameters passed to it as annotations. At the moment it listens for the creation and update of services. This is a structural decision based on my experience and the way Kubernetes expects services to be used. Services are a link between the cluster management plane and the application back-ends (pods). The figure below shows the cert-gen pipeline.

 ![cert-gen: Flow of new certificate.](/posts/k8s/cert-gen/cert-gen-2020-05-04.png)

 Annotations are an easy way to receive information without creating custom resources. The Issuer reference can either be passed via the annotations or via command-line arguments when starting cert-gen. When a service is created or updated cert-gen is notified and looks if the certificate already exists and if not, creates one. When the service is deleted, the certificate and secret are deleted as well (this requires the container-args: `- --enable-certificate-owner-ref=true` in [cert-manager](https://github.com/jetstack/cert-manager/pull/819#issuecomment-613603193)).

The cert-gen repo can be found [here](https://github.com/jonas27test/cert-gen).