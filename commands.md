
```shell
# get all resources
kubectl api-resources --verbs=list --namespaced -o name | xargs -n 1 kubectl get --show-kind --ignore-not-found -A
kubectl get --show-kind --ignore-not-found -A pods

kubectl get all -o wide -A 

kubectl api-versions  # 查看所有apiVersion版本
kubectl api-resources    # 查看所有资源类型


# get all resoures in specific namespace
kubectl get all -n ing-internal

# interact with container
kubectl  exec -it nginx-dp-5dfc689474-7dea /bin/bash

kubectl label pod nginx-pod app=hello
 kubectl label pod nginx-pod app=hello1 --overwrite
```
