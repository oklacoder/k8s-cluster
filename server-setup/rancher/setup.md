### First, install the cert generator ([Link](../cert-issuer/steps.md))

`helm repo add rancher-latest https://releases.rancher.com/server-charts/latest`

`kubectl create namespace cattle-system`

`helm install rancher rancher-latest/rancher --namespace cattle-system --set hostname=rancher.okstovall.com`