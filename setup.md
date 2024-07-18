helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo add jetstack https://charts.jetstack.io --force-update
helm install   cert-manager jetstack/cert-manager   --namespace cert-manager   --create-namespace   --version v1.15.1   --set crds.enabled=true         --set ingressShim.defaultIssuerName=letsencrypt-prod  --set ingressShim.defaultIssuerKind=ClusterIssuer
helm install ingress-nginx ingress-nginx/ingress-nginx

