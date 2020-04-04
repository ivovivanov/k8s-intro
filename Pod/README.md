# POD
## Basic Pod commands
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

View yaml defenition of a running pod
```
kubectl get pod my-pod -o yaml
```
## Pod defenitions
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

---
Environment variables can be set via the pod definition under the containers section:
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-webapp
spec:
  containers:
    - name: flask-webapp
      image: flask
      env:
        - name: debug
          value: true
        - name:
          valueFrom:
            secretKeyRef:
              name: mysecret
              key: username
        - name:
          valueFrom:
            configMapKeyRef:
              name: flask-config
              key: flask-option-1
```
* Instead using `value` environment variable can be set also with `valueFrom` to get the value from ConfigMap or Secret:
