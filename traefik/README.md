https://traefik.io/blog/eks-clusters-with-traefik-proxy-as-the-ingress-controller/

https://brito.com.br/posts/certificados-traefik-cert-manager/

Cluster criado
* eksctl
* helm
* kubectl

deploy traefik

$ helm repo add traefik https://helm.traefik.io/traefik
$ helm repo update

$ helm install traefik traefik/traefik --create-namespace --namespace=traefik --values=traefik-helm-values.yaml

kubectl apply -f traefik-dashboard.yaml

kubectl apply -f 2048.yaml