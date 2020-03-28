# POD
Pod is the smallest working unit in terms of Kubernetes (K8S). A pod can contain one or more containers which share the same starage and network. Containers in a single pod always share the same context and definition.

Pod can be created by:
```
kubectl run my-pod --image=nginx
```
This actually creates a deployment with its replicaset and pod definitions.

Pod can be created also with a pod definition file (pod manifest)
```
kubectl create -f my-pod.yaml
```

---
In pod manmifest files command and args sections can be specified. They reflect specific fields in Dockefile.
| Dockerfile  | Pod Definition |
|-------------|:--------------:|
|  ENTRYPOINT |    command     |
|     CMD     |     args       |


Dockerfile
```
FROM ubuntu
ENTRYPOINT ["sleep"]
CMD ["10"]
```
These parameters can be passed also via the pod definition:
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
    - name: ubuntu-sleep
      image: ubuntu
      command: ["sleep"]
      args: ["10"]
```
