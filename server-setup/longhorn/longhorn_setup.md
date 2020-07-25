
### check longhorn prereqs
>
> `curl -sSfL https://raw.githubusercontent.com/longhorn/longhorn/master/scripts/environment_check.sh | bash`
>

### install longhorn
with helm:
>
> `git clone https://github.com/longhorn/longhorn && cd longhorn`
>
> `kubectl create namespace longhorn-system`
> 
> `helm install longhorn ./chart/ --namespace longhorn-system`
> 
