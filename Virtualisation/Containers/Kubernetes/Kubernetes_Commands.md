# Kubernetes Commands

You can also manage your Kubernetes apps with [Helm](Helm/Helm_Commands.md)

## 🧩Kubernetes Objects🧩

- namespaces
- deployments (deploy)
- statefulset
- services (svc)
- ingress
- persistent volume claim (pvc)
- pods (pod)
- nodes
- jobs (job)

---

## 🎓Basic commands🎓

### Join a namespace

``` bash
kubectl config set-context --current --namespace=[namespace]
```

### List Objects

``` bash
kubectl get [object]
```

Options :

- More info : `-o wide`
- Get YAML format : `-o yaml`
- Get JSON format : `-o json`
- All namespaces : `-A`
- Specific namespace : `-n=[name]`

### Describe Objects

``` bash
kubectl describe [object]
```

### Get YAML definition of an object

``` bash
kubectl get [object] -o yaml
```

### Scale a statefulset/deployment

``` bash
kubectl scale [object] --replicas=[number-of-replicas]
```

### Create an Object form YAML definition

``` bash
kubectl create -f [path-to-file]
```

Options :

- Dry run : `--dry-run=client`

### Update/Create an Object form YAML definition

``` bash
kubectl apply -f [path-to-file]
```

Options :

- Dry run : `--dry-run=client`

---

## 📦Pod commands📦

### Execute command on a pod (Similar to [docker exec](../Docker/Docker_Commands.md#execute-command-in-container) exec)

``` bash
kubectl exec [pod] -- [command]
```

Options :

- Interactive mode : `-it`
- Specify specific container : `-c [container]`

Example :

- `kubectl exec -it [pod] -- bash`

### Copy file inside pod

``` bash
kubectl cp [file-to-copy] [pod]:[where-to-copy]
```

---

## 🎛️Node commands🎛️

### Disable scheduling on a node

``` bash
kubectl cordon [node-name]
```

### Enable scheduling on a node

``` bash
kubectl uncordon [node-name]
```

### See Nodes hardware usage (CPU,MEMORY)

``` bash
kubectl top nodes
```
