# Working with DaemonSets
Daemonset is a special kind of pod that is scheduled on all nodes in k8s
up to v1.12 it used the `NodeName` property
from v1.12 (included) onwards default scheduler is used with `NodeAffinity` rules
## kubectl command
```
kubectl get daemonsets
```
get daemonsets in all namespaces
```
kubectl get daemonsets --all-namespaces
kubectl get daemonsets -A
```
get more verbose output of get command
```
kubectl get daemonsets -o wide
kubectl get daemonsets -o wide --all-namespaces
```
