# ork8suprunning

## Chapter 7. Service Discovery
### The Service Object
#### Readiness Checks
```
kubectl edit deployment/alpaca-prod
```
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


#### Updating a Container Image
```
kubectl rollout status deployments kuard
```

### Deployment Strategies
Two different strategies:
- Recreate
- RollingUpdate

#### Recreate Strategy

#### RollingUpdate Strategy
is capable of talking interchangeably with both a slightly older and a slightly newer version of your software.

#### CONFIGURING A ROLLING UPDATE
Setting maxSurge to 100% is equivalent to a blue/green deployment.

#### Monitering a Deployment
To sethow long the deployment controller should wait before transitioning into this state, use the spec.progressDeadlineSeconds field.
