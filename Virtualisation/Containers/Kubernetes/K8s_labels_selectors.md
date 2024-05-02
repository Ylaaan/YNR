# K8s labels and selectors

## 🚩Labels🚩

Many kubertes objects have labels, they are a regular tag system.

### Definition

You can define as many labels as you want in a ``YAML`` definition.

Example:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: app1
  labels:
    label1: value1
    label2: value2
```

### Label a node

You made want to label a node to be used in [node selectors](./K8s_taints_tolerations_nodeSelector_affinity.md#🧲node-selectors🧲).

```bash
kubectl label node <node-name> key=value
```

### Use

You can then use them as filters in many commands with the ``--selectors key1=value1,key2=value2`` option.

## 💬Annotations💬

Annotations behave more like note fields, additional info not necessarily used by kubernetes or its commands they are definied in a similar manner

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: app1
  labels:
    label1: value1
    label2: value2
  annotations:
    annotation1: value1
```
