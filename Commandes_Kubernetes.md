# **Commandes générales**

### 1. Create resources 

```bash
kubectl create namespace [name_namespace] #utilisée pour créer un namespace dans Kubernetes.
kubectl create -f [name_of_file]
kubectl apply -f [name_of_file]
kubectl run [pod_name] --image=nginx --restart=Never
kubectl run [pod_name] --generator=run-pod/v1 --image=nginx
kubectl run [pod_name] --image=nginx --restart=Never
```
