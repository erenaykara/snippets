list namespaces
```
kubectl get namespace
```

list pods of a namespace
```
kubectl get pods --namespace=core-api
```

connect to a bash of a pod (put pod name instead of core-api-sidekiq-78f6fc6b59-2667v) 
```
kubectl exec --stdin --tty core-api-sidekiq-78f6fc6b59-2667v --namespace=core-api -- /bin/bash
```
