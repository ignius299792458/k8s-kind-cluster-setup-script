# K8s control plane and kubelets based commands

## 1. Namespaces
This gives the detail information about namespaces
```sh
kubectl get ns
# or
kubectl get namespaces

# create
kubectl create namespace <name_of_namespace>

# delete
kubectl delete namespace <name_of_namespace>
```

Result:
```
➜  kubectl get namespaces
NAME                 STATUS   AGE
default              Active   2m43s
kube-node-lease      Active   2m43s
kube-public          Active   2m43s
kube-system          Active   2m43s
local-path-storage   Active   2m39s
```

## 2. Pods ls
Gives all list of pods and control plane
```sh
kubectl get pods
```

## 3. Pods list in certain namespaces
Gives all list of pods and control plane
```sh
kubectl get pods -n <kube_namespace_type_name>
# or as example
kubectl get pods -n kube-system # list all the pods from kube-system namespace
```
Example: 
```
➜  kubectl get pods -n kube-system
NAME                                                       READY   STATUS    RESTARTS   AGE
coredns-668d6bf9bc-7dwfm                                   1/1     Running   0          13m
coredns-668d6bf9bc-9kqhl                                   1/1     Running   0          13m
etcd-ignius-k8s-cluster-control-plane                      1/1     Running   0          13m
kindnet-6q4nw                                              1/1     Running   0          13m
kindnet-6x7fh                                              1/1     Running   0          13m
kindnet-nw7bw                                              1/1     Running   0          13m
kindnet-x5jss                                              1/1     Running   0          13m
kube-apiserver-ignius-k8s-cluster-control-plane            1/1     Running   0          13m
kube-controller-manager-ignius-k8s-cluster-control-plane   1/1     Running   0          13m
kube-proxy-4rsqh                                           1/1     Running   0          13m
kube-proxy-bhxfb                                           1/1     Running   0          13m
kube-proxy-d8fx5                                           1/1     Running   0          13m
kube-proxy-vc5lv                                           1/1     Running   0          13m
kube-scheduler-ignius-k8s-cluster-control-plane            1/1     Running   0          13m
```

## 4. To lunch a pod
This is the way of lunching a pod in defult way. To lunch a pod under certain namespace see point 6.
```sh
kubectl run <container/pod_name> --image=<pod_container_image>
```
Example:
```
# lunch a pod
➜  kubectl run nginx --image=nginx
pod/nginx create

# list pods
➜  kubectl get pods
NAME    READY   STATUS    RESTARTS   AGE
nginx   1/1     Running   0          56s
```

## 5. To delete a pod
if pod is in a wrong namespace or anything issue, we can delete as 
```sh
kubectl delete pod <pod_name>
```
Example
```
# let check if our pod is properly lunched under a required namespace if not delete
➜  kubectl get pods -n nginx
No resources found in nginx namespace.

# Since there is no nginx pod in namespace, so delete it
➜  kubectl delete pod nginx
pod "nginx" deleted
```

## 6. Lunch a pod under a certain namespace
```sh
kubectl run <container/pod_name> --image=<pod_container_image> -n <namespace_name>
```
Example
```
➜  kubectl run nginx --image=nginx -n nginx
Error from server (NotFound): namespaces "nginx" not found

➜  kubectl create namespace nginx
namespace/nginx created

➜  kubectl run nginx --image=nginx -n nginx
pod/nginx created

```

# 7. manifest yml file configuration
Whole k8s `control_plane`, `pods` and `other overall settings of k8s cluster` can be setup completely
under a yml file of configuration name `manifest.yml`






