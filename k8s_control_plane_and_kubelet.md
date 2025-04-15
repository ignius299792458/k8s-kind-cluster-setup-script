# K8s control plane and kubelets based commands

## 1. Namespaces
This gives the detail information about namespaces
```sh
kubectl get ns
# or
kubectl get namespaces
```
Result:
```
➜  kind-k8s-cluster kubectl get namespaces
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
Result: 
```
➜  kind-k8s-cluster kubectl get pods -n kube-system
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

