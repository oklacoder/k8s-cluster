
```bash
helm repo add jetstack https://charts.jetstack.io && \
helm repo update
```

```bash
kubectl create namespace cert-manager && \
helm install cert-manager jetstack/cert-manager --namespace cert-manager --set installCRDs=true
```


Apply with `kubectl apply -f letsencrypt-issuer-staging.yaml`