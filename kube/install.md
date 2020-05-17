# Install in K8s

#### Add ingress
kubectl apply -f https://raw.githubusercontent.com/jonas27/blog/master/kube/ingress.yaml

#### Add jblog service
kubectl apply -f https://raw.githubusercontent.com/jonas27/blog/master/kube/service.yaml

#### Add jblog deployment
kubectl apply -f https://raw.githubusercontent.com/jonas27/blog/master/kube/deployment.yaml
