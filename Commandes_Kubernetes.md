# **Commandes générales**

### 1. Create resources 
**- Create isolation**
```bash
kubectl create namespace [name_namespace] # utilisée pour créer un namespace dans Kubernetes.
```


**- Create pod**
```bash
kubectl create -f [name_of_file] # utilisée pour créer le nom de file dans Kubernetes.
kubectl apply -f [name_of_file] # sert à appliquer ou mettre à jour la configuration des ressources Kubernetes
kubectl run [pod_name] --image=nginx --restart=Never # sert à créer un pod unique dans Kubernetes, basé sur l'image spécifiée (nginx).
```

**- Create Service**
```bash
kubectl create svc nodeport [svc_name] --tcp=8080:80 # permet d'exposer et de gérer l'accès réseau aux pods ou aux ressources à l'intérieur du cluster Kubernetes.
```

### 2. Viewing and finding resources

**-Namespaces**
```bash
kubectl get ns # permet de lister tous les namespaces
kubectl get ns -o yaml # permet de lister tous les namespaces dans le cluster Kubernetes et d'afficher les informations de chaque namespace au format YAML. 
kubectl describe ns # fournit des détails approfondis sur un namespace spécifique dans Kubernetes.
```
- namespaces, abbreviation: ns
  
**- Deployments**
```bash
kubectl get deploy # permet de lister tous les déploiements dans le cluster Kubernetes.
kubectl describe deploy # fournit des détails approfondis sur un déploiement spécifique dans Kubernetes.
kubectl get deploy -o wide # permet de lister les déploiements dans le cluster Kubernetes, tout en fournissant des informations supplémentaires.
kubectl get deploy -o yaml # permet de lister les déploiements dans le cluster Kubernetes et d'afficher les détails du déploiement sous le format YAML. 
```
**- Pods**
```bash
kubectl get po # Afficher toutes les informations sur les groupes de conteneurs
kubectl get po -o wide # permet de lister tous les pods dans le cluster Kubernetes et d'afficher des informations supplémentaires.
kubectl describe po # permet d'afficher des informations détaillées sur un pod spécifique dans Kubernetes.
kubectl get po --show-labels # Voir les étiquettes du groupe de conteneurs.
kubectl get po -l app=nginx # permet d'afficher des informations détaillées sur un pod spécifique dans Kubernetes.
kubectl get po -o yaml # permet de lister les pods dans le cluster Kubernetes et d'afficher leurs informations au format YAML. 
kubectl get pod [pod_name] -o yaml --export # permet d'exporter la configuration YAML d'un pod sans les métadonnées spécifiques au cluster.
kubectl get pod [pod_name] -o yaml --export > nameoffile.yaml # Exporter les informations du groupe de conteneurs vers un fichier yaml au format yaml.
kubectl get pods --field-selector status.phase=Running # Utiliser le sélecteur de champs pour filtrer les informations du groupe de conteneurs.
```
- deployments, abbreviation: deploy

**- Nodes**
```bash
kubectl get no # Afficher toutes les informations sur les nodes.
kubectl get no -o wide # Afficher plus d'informations sur tous les nodes.
kubectl describe no # permet d'afficher des informations détaillées sur un nœud spécifique dans un cluster Kubernetes.
kubectl get no -o yaml # permet d'afficher des informations détaillées sur un nodes spécifique dans un cluster Kubernetes. 
kubectl get node --selector=[label_name] # Pour filtrer les nodes d'un cluster Kubernetes en fonction d'un label spécifique
kubectl get nodes -o jsonpath='{.items[*].status.addresses[?(@.type="ExternalIP")].address}' #Pour afficher des informations spécifiques d'un objet Kubernetes en utilisant une expression JSONPath.
kubectl top node [node_name] # Display node (CPU/memory/storage) usage # permet d'afficher l'utilisation des ressources (CPU et mémoire) d'un nœud spécifique dans un cluster Kubernetes. 
```
- nodes, abbreviation: no

**- Service**
```bash
kubectl get svc # permet d'afficher la liste des services dans le cluster Kubernetes actuel.
kubectl describe svc # permet d'afficher des informations détaillées sur un service spécifique dans un cluster Kubernetes. 
kubectl get svc -o wide # permet d'afficher la liste des services dans le cluster Kubernetes actuel avec des informations supplémentaires
kubectl get svc -o yaml # permet d'afficher la configuration complète d'un ou de plusieurs services dans le cluster Kubernetes actuel au format YAML.
kubectl get svc --show-labels # permet d'afficher la liste des services dans le cluster Kubernetes actuel, en incluant une colonne supplémentaire intitulée LABELS
```
- services, abbreviation: svc

**- Roles**
```bash
kubectl get roles --all-namespaces # permet d'afficher la liste de tous les objets Role dans l'ensemble des namespaces de votre cluster Kubernetes.
kubectl get roles --all-namespaces -o yaml # permet d'afficher la liste de tous les objets Role dans l'ensemble des namespaces de votre cluster Kubernetes, au format YAML.
```

**- Ingress**
```bash
kubectl get ing # permet d'afficher la liste des objets Ingress dans le namespace actuel de votre cluster Kubernetes.
kubectl get ing --all-namespaces # permet d'afficher la liste de tous les objets Ingress dans l'ensemble des namespaces de votre cluster Kubernetes.
```
- ingresses, abbreviation: ing

**- Persistent Volumes**
```bash
kubectl get pv # permet d'afficher la liste des Persistent Volumes (PV) dans votre cluster Kubernetes.
kubectl describe pv #  permet d'afficher des informations détaillées sur un ou plusieurs Persistent Volumes (PV) dans votre cluster Kubernetes.
```
- persistentvolume, abbreviation: pv

**- Persistent Volumes Claims**
```bash
kubectl get pvc # permet d'afficher la liste des Persistent Volumes Claims (PVC) dans votre cluster Kubernetes.
kubectl describe pvc #  permet d'afficher des informations détaillées sur un ou plusieurs Persistent Volumes Claims (PVC) dans votre cluster Kubernetes.
```
- persistentvolumeclaims, abbreviation: pvc

**- storage class**

```bash
kubectl get sc # permet d'afficher la liste des Storage Classes dans votre cluster Kubernetes.
kubectl get sc -o yaml # permet d'afficher la liste des Storage Classes dans votre cluster Kubernetes au format YAML.
```

### 3.Updating resources

**- Node/Pod**
```bash
kubectl delete node [node_name] # permet de supprimer un nœud spécifique de votre cluster Kubernetes.
kubectl delete pod [pod_name] # permet de supprimer un pod spécifique de votre cluster Kubernetes.
kubectl edit node [node_name] # permet d'ouvrir un éditeur pour modifier la configuration d'un nœud spécifique dans votre cluster Kubernetes.
kubectl edit pod [pod_name] # permet d'ouvrir un éditeur pour modifier la configuration d'un pod spécifique dans votre cluster Kubernetes.
```
**- Namespace**
```bash
kubectl edit deploy [deploy_name] #  permet d'ouvrir un éditeur pour modifier la configuration d'un pod spécifique dans votre cluster Kubernetes.
kubectl delete deploy [deploy_name] # permet de supprimer un déploiement spécifique dans votre cluster Kubernetes.
kubectl expose deploy [deploy_name] --port=80 --type=NodePort # crée un service de type NodePort qui expose le déploiement spécifié sur le port 80.
kubectl scale deploy [deploy_name] --replicas=5 # permet de modifier le nombre de réplicas (instances) d'un déploiement spécifique dans votre cluster Kubernetes.
kubectl delete ns # permet de modifier le nombre de réplicas (instances) d'un déploiement spécifique dans votre cluster Kubernetes.
kubectl edit ns [ns_name] # permet d'ouvrir un éditeur pour modifier la configuration d'un namespace spécifique dans votre cluster Kubernetes.
```


