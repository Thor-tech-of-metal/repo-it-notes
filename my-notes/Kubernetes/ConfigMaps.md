Mounted ConfigMaps
===================
Mounted ConfigMaps are updated automatically
When a ConfigMap currently consumed in a volume is updated, projected keys are eventually updated as well. The kubelet checks whether the mounted ConfigMap is fresh on every periodic sync. However, 
the kubelet uses its local cache for getting the current value of the ConfigMap

```
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
  containers:
  - name: mypod
    image: redis
    volumeMounts:
    - name: foo
      mountPath: "/etc/foo"
      readOnly: true
  volumes:
  - name: foo
    configMap:
      name: myconfigmap
```
The following ConfigMap (myconfigmap.yaml) stores two properties: username and access_level:
```
apiVersion: v1
kind: ConfigMap
metadata:
  name: myconfigmap
data:
  username: k8s-admin
  access_level: "1"
```

```
kubectl apply -f myconfigmap.yaml
```
The following Pod consumes the content of the ConfigMap as environment variables:

configmap/env-configmap.yaml
```
apiVersion: v1
kind: Pod
metadata:
  name: env-configmap
spec:
  containers:
    - name: app
      command: ["/bin/sh", "-c", "printenv"]
      image: busybox:latest
      envFrom:
        - configMapRef:
            name: myconfigmap
```

```
kubectl apply -f env-configmap.yaml
```

```
kubectl logs pod/env-configmap
```

The output is similar to this:

```
username: "k8s-admin"
access_level: "1"
```


