# Create PerconaXtraDB database with startup script

```yaml
apiVersion: kubedb.com/v1alpha1
kind: PerconaXtraDB
metadata:
  name: px-init-script
  namespace: demo
spec:
  version: "5.7"
  replicas: 1
  storageType: Durable
  storage:
    storageClassName: "standard"
    accessModes:
    - ReadWriteOnce
    resources:
      requests:
        storage: 50Mi
  init:
    scriptSource:
      configMap:
        name: px-init-script
  updateStrategy:
    type: "RollingUpdate"
  terminationPolicy: DoNotTerminate
```
