# Working with Custom Schedulers
Custom Scheduler can be running on the same node(s) as the default Scheduler.
Names of the schedulers should be different. Schedulers can run as a service or as a pod within a Kubernetes cluster.
Default manifest directory is `/etc/kubernetes/manifests` (This is valid when sheduler is running as a pod).

## When shedulers are running as pods usually they are in the kube-system namespace
```
kubectl get pods -n kube-system
```

get name of docker image of a sheduler. In this case pod name is `kube-scheduler-master`
```
kubectl describe pod kube-scheduler-master -n kube-system |grep -i 'Image:'
```
