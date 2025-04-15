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

