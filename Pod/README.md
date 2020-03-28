# POD
Pod is the smallest working unit in terms of Kubernetes (K8S). A pod can contain one or more container which share the same namespace and network.

Pod can be created by:
```
kubectl run my-pod --image=nginx
```
This actually creates a deployment with its replicaset and pod definitions.

Pod can be created also with a pod definition file (pod manifest)
```
kubectl create -f my-pod.yaml
```
