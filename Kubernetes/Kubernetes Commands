## Kubernetes Objects

 - namespaces
 - deployments (deploy)
 - statefulset
 - services (svc)
 - persistent volume claim (pvc)
 - pods (pod)
 - nodes
 
---

## Basic commands

##### Join a namespace :
``` bash
kubectl config set-context --current --namespace=[namespace]
```

##### List Objects
``` bash
kubectl get [object]
```

Options : 
- More info : `-o wide`
- All namespaces : `-A`
- Specific namespace : `-n=[name]`

##### Describe Objects
``` bash
kubectl describe [object]
```

##### Get YAML definition of an object
``` bash 
kubectl get [object] -o yaml
```

##### Scale a statefulset/deployment
``` bash
kubectl scale [object] --replicas=[number-of-replicas]
```

---

## Pod commands

##### Execute command on a pod (Similar to [[Docker Commands#Execute command in container :|Docker]] exec)

``` bash
kubectl exec [pod] -- [command]
```

Options :
- Interactive mode : `-it`
- Specify specific container : `-c [container]`

Example :
- `kubectl exec -it [pod] -- bash`

##### Copy file inside pod
``` bash
kubectl cp [file-to-copy] [pod]:[where-to-copy]
```

---

## Node commands

##### Disable scheduling on a node

``` bash
kubectl cordon [node-name]
```

##### Enable scheduling on a node

``` bash
kubectl uncordon [node-name]
```

##### See Nodes hardware usage (CPU,MEMORY)

``` bash
kubectl top nodes
```
