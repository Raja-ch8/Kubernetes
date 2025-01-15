# **Commandes générales**

### 1. Create resources 
**- Create pod**
```bash
kubectl create namespace [name_namespace] #utilisée pour créer un namespace dans Kubernetes.
kubectl create -f [name_of_file] #utilisée pour créer le nom de file dans Kubernetes.
kubectl apply -f [name_of_file] #sert à appliquer ou mettre à jour la configuration des ressources Kubernetes
kubectl run [pod_name] --image=nginx --restart=Never #sert à créer un pod unique dans Kubernetes, basé sur l'image spécifiée (nginx).
```

### 2. Create Service

```bash
kubectl create svc nodeport [svc_name] --tcp=8080:80 #permet d'exposer et de gérer l'accès réseau aux pods ou aux ressources à l'intérieur du cluster Kubernetes.

```

### 3. Viewing and finding resources

```bash


```
