# Static Pod
This is a feature of the kubelet to run pods on its own without having master(Api Server)

---
Kubelet check a path for pod yaml manifest files and runs the pod also if they crash kubelet is trying to restar the pod
Path to stati pod manifest files if configured in
- kubelet.service (`--pod-manifest-path` option is used)
- configuration file that is provided as a path in the kubelet.service (with `--config` option).
    use the `staticPodPath` record in this config file
--- 
If an Api Server recognize a Static Pod it creates a mirror of it in the etcd datastore.
Staic Pods are ignored by the Kube-Scheduler 

---
Static pods are recognized when runing `kubectl get pods` by their name - it always ends with the name of the node:

- podnname-master
- podname-node01
