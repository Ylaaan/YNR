# K8s Daemon sets

A daemon set is a deployment that will create a copy of the application on every node.

## Overview

```mermaid
flowchart LR
    YAML_definition["YAML definition"] --> API
    subgraph Cluster
      subgraph Master
          API
      end
      subgraph Node1
          DaemonSet1["DaemonSet"]
      end
      subgraph Node2
          DaemonSet2["DaemonSet"]
      end
      subgraph Node3
          DaemonSet3["DaemonSet"]
      end
      API--> DaemonSet1 & DaemonSet2 & DaemonSet3
    end
```

## Definition

Example:

```yaml
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: app1
spec:
  selector:
    matchLabels:
      app: app1
  template:
    metadata:
      labels:
       app: app1
    spec:
      containers:
      - name: app1
        image: image1
```
