# All the cmds related to the manifest file handling

## 1. create and apply a namespace from namespace.yml config
```
~ kubectl apply -f namespace.yml 
  namespace/nginx created
```

## 2. create and apply a pod from pod.yml config
```
~ kubectl apply -f pod.yml 
  pod/nginx-pod created
```

## 3. Going to shell of pod alike container shell
```sh
kubectl exec -it <pod_name> -n <namespace> -- bash 
```
Example
```
~ kubectl exec -it nginx-pod -n nginx -- bash
root@nginx-pod:/# curl 127.0.0.1
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

## 4. Describe whole lifecycle of pod from creation to deletion
```sh
kubectl describe pod/<pod_name> -n <namespace>
```

Example
```
~ kubectl describe pod/nginx-pod -n nginx

Name:             nginx-pod
Namespace:        nginx
Priority:         0
Service Account:  default
Node:             ignius-k8s-cluster-worker3/172.18.0.4
Start Time:       Tue, 15 Apr 2025 21:41:50 +0545
Labels:           <none>
Annotations:      <none>
Status:           Running
IP:               10.244.3.4
IPs:
  IP:  10.244.3.4
Containers:
  nginx:
    Container ID:   containerd://23b5fc2c46603e97b2c8929c123c697c06fb096d0c7fac658fd0bcd7f45c9378
    Image:          nginx:latest
    Image ID:       docker.io/library/nginx@sha256:09369da6b10306312cd908661320086bf87fbae1b6b0c49a1f50ba531fef2eab
    Port:           80/TCP
    Host Port:      0/TCP
    State:          Running
      Started:      Tue, 15 Apr 2025 21:41:52 +0545
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-6cr5n (ro)
Conditions:
  Type                        Status
  PodReadyToStartContainers   True 
  Initialized                 True 
  Ready                       True 
  ContainersReady             True 
  PodScheduled                True 
Volumes:
  kube-api-access-6cr5n:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
QoS Class:                   BestEffort
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type    Reason     Age    From               Message
  ----    ------     ----   ----               -------
  Normal  Scheduled  4m53s  default-scheduler  Successfully assigned nginx/nginx-pod to ignius-k8s-cluster-worker3
  Normal  Pulling    4m53s  kubelet            Pulling image "nginx:latest"
  Normal  Pulled     4m51s  kubelet            Successfully pulled image "nginx:latest" in 2.231s (2.231s including waiting). Image size: 68655620 bytes.
  Normal  Created    4m51s  kubelet            Created container: nginx
  Normal  Started    4m51s  kubelet            Started container nginx

```

