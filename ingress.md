
### Ingress-nginx

https://kubernetes.github.io/ingress-nginx/deploy/


kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.8.1/deploy/static/provider/cloud/deploy.yaml

kubectl edit pods -n ingress-nginx ingress-nginx-controller-58fb7887bb-xhgqw

Add hostNetwork: true to controller pod

```yaml
        image: registry.cn-beijing.aliyuncs.com/damon_registry/cka:controller-v1.8.1 
        imagePullPolicy: IfNotPresent
        lifecycle:
          preStop:
            exec:
              command:
              - /wait-shutdown
        livenessProbe:
          failureThreshold: 5
          httpGet:
            path: /healthz
            port: 10254
            scheme: HTTP
          initialDelaySeconds: 10
          periodSeconds: 10
          successThreshold: 1
          timeoutSeconds: 1
        name: controller
        hostNetwork: true
```

For network issue
	修改控制器的image为：registry.cn-beijing.aliyuncs.com/damon_registry/cka:controller-v1.8.1
	
	修改webhook的image为：registry.cn-beijing.aliyuncs.com/damon_registry/cka:kube-webhook-certgen-v20230407


### IngressClass 
https://kubernetes.io/zh-cn/docs/reference/kubernetes-api/service-resources/ingress-class-v1/#IngressClass
```
注意事项：
# 可以在nginx的ingressclass设置为默认，添加如下annotation
kubectl edit ingressclasses.networking.k8s.io nginx
annotations:
    ingressclass.kubernetes.io/is-default-class: "true"

# 如果没有设置ingressclass默认值，可以在创建ingress时，添加一下参数指定ingressclassname
ingressClassName: nginx
```
