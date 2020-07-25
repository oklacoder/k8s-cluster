# Commands

## basic setup

### Generate ssh key
> `ssh-keygen`
>
> (`enter`)
>
> (`enter`)
>
> (`enter`)

### Propagate ssh key
> `ssh-copy-id {user}@{utilityNode}`
>
> `yes`
>
> `{password}`


repeat for each k8s node:
>
> `ssh-copy-id {user}@{node}`
>
> `yes`
>
> `{password}`

### enable passwordless sudo 
repeat on each node:
>
> `sudo visudo`
>
> insert at end: 
> 
> `{user} ALL=(ALL) NOPASSWD: ALL`

### disable swap for k8s
repeat on each node:
>
> `sudo nano /etc/fstab`
>
> remove every line that contain the word "swap"

### increase virtual memory for Elastic
repeat on each nod:
>
> `sudo nano /etc/sysctl.conf`
>
> insert at end: 
>
> `vm.max_map_count=262144`


> `sudo reboot`

### install k3sup
>
> `curl -sLS https://get.k3sup.dev | sh`
>
> `sudo install k3sup /usr/local/bin/`

### install k3s master node
>
> `k3sup install --ip {master id} --user {user}`
> 
> save ca and user data for ~/.kube/.config

LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUJXRENCL3FBREFnRUNBZ0VBTUFvR0NDcUdTTTQ5QkFNQ01DTXhJVEFmQmdOVkJBTU1HR3N6Y3kxelpYSjIKWlhJdFkyRkFNVFU1TlRRME5UUTRNVEFlRncweU1EQTNNakl4T1RFNE1ERmFGdzB6TURBM01qQXhPVEU0TURGYQpNQ014SVRBZkJnTlZCQU1NR0dzemN5MXpaWEoyWlhJdFkyRkFNVFU1TlRRME5UUTRNVEJaTUJNR0J5cUdTTTQ5CkFnRUdDQ3FHU000OUF3RUhBMElBQkZmcGwzMXdyTjkweVJ2L3h2WEdTckxpSHZZNmxXZkFlUDFKUWh2ZmRWVUsKWnpqR2dBSjlja2pDYjhiUExXTDhHTlRNWkNCa2UwY1RKdVdNMlphcG5RS2pJekFoTUE0R0ExVWREd0VCL3dRRQpBd0lDcERBUEJnTlZIUk1CQWY4RUJUQURBUUgvTUFvR0NDcUdTTTQ5QkFNQ0Ewa0FNRVlDSVFEZzc3UW02QjgyCmVXaGhzVzBZTDc5QmoxS1BmVkgveGk0bDBLclArSHlySlFJaEFKR1JacFRqOGNQZldiZUJLT1JJUkd2ZFRtNnoKLy9XQU40ZGx2RE5KNVM3OQotLS0tLUVORCBDRVJUSUZJQ0FURS0tLS0tCg==

password: 8ceb80bc9e42f2b407d4f3947cfdad93

username: admin

>
> `k3sup join --ip {worker ip} --server-ip {master ip} --user {user}`
>

## longhorn setup
https://longhorn.io/docs/0.8.1/deploy/install/

### check cluster status
> `export KUBECONFIG=`pwd`/kubeconfig`
> `kubectl get node -o wide`
