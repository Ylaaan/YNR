# K8s taints,node selector,affinity

## 🎨Taints🎨

A taint doesn't tell a pod to go to a node. It only tells pods NOT to go to one. By default the master nodes has taints to prevent regular pods to run on it.

### Taint a node

```bash
kubectl taint nodes <node-name> key=value:{NoSchedule|PreferNoSchedule|NoExecute}
```

Note:

- Adding a `-` to the end of an existing taint will delete it from the node.
- `NoSchedule` will prevent new pods from being scheduled.
- `NoExecute` will kill current pods without the toleration on the node

## 🆗Toleration🆗

Set in the definition.

Example:

```yaml
apiVersion: v1
kind: Pod
metadata:
    name: app1
spec:
  containers:
  - name: app1
    image: image1
  tolerations:
  - key: "key"
    operator: "Equal"
    value: "value1"
    effect: "NoSchedule"
```

## 🧲Node selectors🧲

A node selector is a way of telling the scheduler to put a pod in a specific node. You can definite that node selector in the definition of the pod.

Example:

```yaml
apiVersion: v1
kind: Pod
metadata:
    name: app1
spec:
  containers:
  - name: app1
    image: image1
  nodeSelector:
    key: value
```

The `key: value` pair used here is a [label](./K8s_labels_selectors.md#label-a-node) defined on nodes.

## Node affinity

Node affinity if a finer way of controlling wich pod is schedules on which node. With parameters such as `in`,`not in`,`if`,`or`...

They can still be set in the definition although they are more complex.

Example:

```yaml
apiVersion: v1
kind: Pod
metadata:
    name: app1
spec:
  containers:
  - name: app1
    image: image1
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
        - matchExpressions:
          - key: key
            operator: In
            values:
            - value1
            - value2
```

More about node affinity [here](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#node-affinity).
