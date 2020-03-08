# ork8suprunning


## Chapter 10.Deployments
### Your First Deployment
#### Deployment Internals
```
kubectl get deployments kuard -o jsonpath --template {.spec.selector.matchLabels}
```
```
kubectl get replicasets --selector=run=kuard
```
```
kubectl scale deployments kuard --replicas=2
```

If you ever want to manage that ReplicaSet directly, you need to delete the deployment (remember to set --cascade to false, or else it will delete the ReplicaSet and Pods as well!).

### Creating Deployments
```
kubectl get deployments kuard --export -o yaml > kuard-deployment.yaml
```

### Managing Deployments
```
kubectl describe deployments kuard
```
```
kubectl rollout history
```

### Updating Deployments
```
kubectl rollout status
```

### Deployment Strategies
Two different strategies:
- Recreate
- RollingUpdate

#### Recreate Strategy
