# k8s-kind-cluster-script

The process of lunching the `kubernetes` IN `docker`, this is technique is named `K-IN-D` kind.

## `shell command`
	
1. Create a cluster according to config.yml
		
```shell
kind create cluster --name=<our_k82_cluster_name> --config=config.yml
```
Result:

```
~ kind create cluster --name=ignius-k8s-cluster --config=config.yml

Creating cluster "ignius-k8s-cluster" ...
 ✓ Ensuring node image (kindest/node:v1.32.2) 🖼 
 ✓ Preparing nodes 📦 📦 📦 📦  
 ✓ Writing configuration 📜 
 ✓ Starting control-plane 🕹️ 
 ✓ Installing CNI 🔌 
 ✓ Installing StorageClass 💾 
 ✓ Joining worker nodes 🚜
 .....

```

2. Delete a kind cluster

```shell
kind delete cluster --name <our_kind_k82_cluster_name>
```

3. Cluster information 

```shell
kubectl cluster-info --context <our_k8s_cluster_name>
```




