```
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo add jetstack https://charts.jetstack.io --force-update
kubectl create ns nginx-ingress
helm install ingress-nginx ingress-nginx/ingress-nginx --namespace nginx-ingress --set controller.ingressClassResource.default=true
helm install   cert-manager jetstack/cert-manager   --namespace cert-manager   --create-namespace   --version v1.15.1   --set crds.enabled=true         --set ingressShim.defaultIssuerName=letsencrypt-prod  --set ingressShim.defaultIssuerKind=ClusterIssuer
```

```
kubectl apply -f certsetup.yaml
kubect describe service -n ingress-nginx
# Set up DNS records based on External IP
# Then once everything is working...
kubectl delete namespace testing
```
