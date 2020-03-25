# Logging and Monitoring

---

## Metrics Server
Get metrics from Pods and Nodes. It stores its data only in memmory. Thus no historical data will be available. It heavily relies on Kubelet's subcomponent - cAdvisor.
 -  for minikube
```
minikube addons enable metrics-server
```
 - for fully-fledged environment clone from git and create deployment

Get metrics:
 - `kubectl top nodes` - metrics for nodes
 - `kubectl top nodes` - metrics for pods
---

## Logging

View pod logs

```
kubectl logs my-pod
```
Stream logs of pod live
```
kubectl logs -f my-pod
```

*Remark - multiple containers can run in single pod*
