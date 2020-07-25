# access longhorn dashboard
create an ingress, similar to this, and `kubectl apply -f {path}` it

```
apiVersion: networking.k8s.io/v1beta1
kind: Ingress
metadata:
  name: longhorn-ui-ingress
  namespace: longhorn-system
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /
spec:
  backend:
    serviceName: longhorn-frontend
    servicePort: 80
```
it should then be available at `http://{ingress controller address:port}/longhorn`