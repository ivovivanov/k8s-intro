# ConfigMaps
ConfigMap is a way to set environment variable. This can be done also with `env` property in a container section in pod defenition files
example setting two environment variables:
```yaml
env:
  - name: DB_PORT
    value: 3306
  - name: DEBUG_LEVEL
    value: info
```
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
or
ConfigMaps can be attached as volumes
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
Create ConfigMap with defenition file
```
kubectl create -f config-map.yaml
```
