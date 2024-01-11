https://blog.saeloun.com/2023/03/21/setup-nginx-ingress-aws-eks/

# Add HELM Repository
```
$ helm repo add nginx-stable https://helm.nginx.com/stable
$ helm repo update
```

# Install the Nginx Controller
helm upgrade --install ingress-nginx ingress-nginx \
             --repo https://kubernetes.github.io/ingress-nginx \
             --namespace ingress-nginx --create-namespace

```
kubectl get pods -n ingress-nginx
NAME                                        READY   STATUS      RESTARTS    AGE
ingress-nginx-controller-89758f7c6-swwpf    1/1     Running     0           1m
```
Verify, the LoadBalancer is set up.

```
kubectl get services -n ingress-nginx
NAME                                 TYPE           CLUSTER-IP       EXTERNAL-IP                                                              PORT(S)                      AGE
ingress-nginx-controller             LoadBalancer   10.100.20.84     a4217761afdb3457683821e38a3d3de7-XXXXXXXXX.us-east-2.elb.amazonaws.com   80:31105/TCP,443:31746/TCP   3d18h
Note down the External-IP, this will be used to map the domain name to the LoadBalancer. In our case a4217761afdb3457683821e38a3d3de7-XXXXXXXXX.us-east-2.elb.amazonaws.com
```

10014  eksctl create cluster -f cluster-advanced.yaml
10024* aws eks update-kubeconfig --region us-east-1 --name k8s
10026* kubectl get nodes

10034  helm repo add nginx-stable https://helm.nginx.com/stable
10035  helm repo update
10036  helm upgrade --install ingress-nginx ingress-nginx --repo https://kubernetes.github.io/ingress-nginx --namespace ingress-nginx --create-namespace
10037* kubectl get pods -n ingress-nginx
10038* kubectl --namespace ingress-nginx get services -o wide -w ingress-nginx-controller
10039  kubectl get svc -n ingress-nginx
10040  kubectl apply -f nginx-ingress-controller/2048.yaml
10041  kubectl get pods
10042  kubectl get svc
10043  kubectl get ingress

10067  helm repo add jetstack https://charts.jetstack.io
10068  helm repo update
10069  helm install cert-manager jetstack/cert-manager --namespace cert-manager --create-namespace --version v1.13.1 --set installCRDs=true
10070  kubectl apply -f nginx-ingress-controller/cluster-issuer.yaml
10071  kubectl get pods -n cert-manager

10098  kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
10099  kubectl top nodes
10104  eksctl upgrade cluster -n k8s -r us-east-1 --version 1.28

10118  eksctl upgrade nodegroup --name default --kubernetes-version 1.28 --cluster k8s
10119* watch kubectl get nodes
10120  eksctl delete cluster -f cluster-advanced.yaml
