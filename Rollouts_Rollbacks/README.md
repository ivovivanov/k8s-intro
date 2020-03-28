# Rollouts
# Rollouts and Deployments
When you deployment is created it triggers a rollout. When new rollout is triggered it creates a new deployment revision. This also enables users to be able to rollback to a previous revision(version of the deployment) if neccessary.

Show the status of a rollout
```
kubectl rollout status deplpoyment/my-deployment
```
Show the reviosion history
```
kubectl rollout history deplpoyment/my-deployment
```
---
## Deployment Strategies

### ***Recreate Strategy***
This is not the default deployment strategy. When recreate strategy is used all the pods are destroyed and afterwards newer version pods are created. This causes application downtime.

### ***Rolling Update***
This is the default deployment strategy. When Rolling Updatestrategy is used older pods are destroyed one by one while newer version pods are created one be one. When an old pod is destroyed an instance of the newer ones is created and then it starts to destroy the next of the older pods.

---
In the Events section of the output of the describe command it is clearly shown which deployment strategy is being used. If all the pods are first destroyed and after that the newer pods are being creted then this indicates a Recreate Deployment strategy and not Rolling Update strategy.
```
kubectl describe deployment my-deployment
```
## Rolling Out

Rollout with a new version of the deployment manifest file:
```
kubectl create -f deployment-defenition.yml
```
The set image command can also be used but then the workign version is different compared to the one present in the deployment defenition manifest file:
```
kubectl set image deployment/my-deployment nginx=nginx:1.9.1
```
K8S creates a new replicaset behind the scenes in order to have the desired number of the newer pods while destroyng the old pods from the current replicaset. This can be viewed with the folling command(while the upgrade is being triggered):
```
kubectl get replicasets
```
## Rolling Back

Rollout can always be reverted to the previous version(if this is neccessary) with the command:
```
kubectl rollout undo deployment/my-deployment
```
or to a specified revision:
```
kubectl rollout undo deployment/my-deployment --to-revision=2
```
