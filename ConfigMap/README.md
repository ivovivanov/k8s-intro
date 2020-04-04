# Working with ConfigMaps
ConfigMap is a way to set environment variable. This cna be done also with `env` property in the containers section in pod defenition files
example setting two environment variables:
```yaml
env:
  - name: DB_PORT
    value: 3306
  - name: DEBUG_LEVEL
    value: info
```
## ConfgMaps
Under the same `env` property environment variables can be set with ConfigMaps
```yaml
env:
  - name: DB_PORT
    valueFrom:
      configMapKeyRef:
        name: my-config-map
        key: DB_PORT
```
or
```yaml
envFrom:
  - configMapRef:
      name: my-config-map
```
## Working with ConfigMaps
List ConfigMaps
```
kubectl get configmaps
```
Get info for a configmapr
```
kubectl describe configmap my-config-map
```
## Creating ConfigMaps
### Inmeprative
Create ConfigMap with kubectl command
 - with literals
```
kubectl create configmap my-config-map --from-literal=DB_PORT:3306 --from-literal=DEBUG_LEVEL=info
```
 - from file
```
kubectl create configmap my-config-map --from_file=my-app.config
```

### Declarative
Create ConfigMap with defenetion file
```
kubectl create -f config-map.yaml
```
