
```shell
# get all resources
kubectl api-resources --verbs=list --namespaced -o name | xargs -n 1 kubectl get --show-kind --ignore-not-found -A
kubectl get all -o wide -A 

kubectl api-versions  # 查看所有apiVersion版本
kubectl api-resources    # 查看所有资源类型


# get all resoures in specific namespace
kubectl get all -n ing-internal

```
