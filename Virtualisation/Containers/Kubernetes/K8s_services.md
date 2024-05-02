# K8s Services

## Definition

You can define a service with a YAML file:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app.kubernetes.io/name: MyApp
  ports:
    - protocol: TCP
      port: 80
      targetPort: 9376
```

This will apply to all pods with the correponding label present in the selector field.

There are many services type, you can get [more info here.](https://kubernetes.io/docs/concepts/services-networking/service)
