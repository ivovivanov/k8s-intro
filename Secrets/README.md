# Secrets
Secret is a way to set environment variable and/or sensitive data. Secrets are not encrypted but rather BASE64 encoded. 
The `env` property in a container section 
```yaml
env:
  - name: DB_PORT
    valueFrom:
      secretKeyRef:
        name: my-secret
        key: password
```
or
```yaml
envFrom:
  - secretRef:
      name: my-secret
```
or
secrets can be attached as volumes
## Working with Secrets
List Secrets
```
kubectl get secrets
kubectl get secrets my-secret -o yaml
```
Get info for a secret
```
kubectl describe secret my-secret
```
## Creating Secrets
### Inmeprative
Create secret with kubectl command
 - with literals
```
kubectl create secret generic my-secret --from-literal=username:ivo --from-literal=password=Th1sp@$$
```
 - from file
```
kubectl create secret generic my-secret --from_file=my-secrets.config
```

### Declarative
Create secret with defenition file. Values should be specified in BASE64 in the secret defenition file.
A way to encode in BASE64 is `echo -n 'passwordstring'| base64` :

```
kubectl create -f config-map.yaml
```
