# *KUBERNETES EN LOCAL*

Pour utiliser Kubernetes, il est essentiel de disposer d'une infrastructure permettant d'exécuter les composants du cluster, car Kubernetes a besoin d'un environnement pour orchestrer les conteneurs et gérer les ressources. Cet environnement peut être un serveur physique, une machine virtuelle ou une solution locale. Voici les options disponibles :

### **1. Kubernetes nécessite un serveur ou une infrastructure**
Kubernetes est conçu pour gérer les conteneurs dans un cluster distribué. Cela implique généralement l'utilisation de :

**Serveurs physiques** (bare-metal) : Des machines physiques dédiées.
**Serveurs virtuels** : Par exemple, des machines virtuelles hébergées sur VMware, Hyper-V ou dans le cloud.
**Cloud** : Comme Google Kubernetes Engine (GKE), Amazon EKS ou Azure AKS.

### **2. Solutions pour utiliser Kubernetes en local**
Pour ceux qui ne disposent pas de serveurs dédiés ou qui souhaitent expérimenter Kubernetes facilement, il existe des solutions permettant de configurer et d'utiliser Kubernetes en local, en simulant un cluster sur une machine personnelle. Ces options sont idéales pour les développeurs et ceux qui souhaitent apprendre.

**- Principales options pour un usage local :**

**Minikube :**
- Simule un cluster Kubernetes complet sur une machine locale.
- Idéal pour les tests et le développement.
- Supporte des pilotes comme Docker, VirtualBox et Hyper-V.

**Kind (Kubernetes IN Docker) :**
- Exécute Kubernetes dans des conteneurs Docker.
- Léger et rapide pour tester des applications Kubernetes.

**MicroK8s :**
- Une installation minimale et prête à l'emploi de Kubernetes.
- Parfait pour les utilisateurs Linux (disponible également sur macOS et Windows via Multipass).

**k3s :**
- Une distribution légère et simplifiée de Kubernetes.
- Idéal pour les systèmes avec des ressources limitées.

## **3. Installation des outils locaux**
Avant d'installer un outil Kubernetes, assurez-vous d'avoir :

## **1 - Installez Docker :**
Installez Docker sur votre système macOS/Linux: `brew install docker`
Installez Docker sur votre système Ubuntu:

A) - Tout d'abord, il est nécessaire de mettre à jour le cache des paquets en exécutant
la commande suivante avec des privilèges d'administrateur :

```bash
sudo apt-get update
```

B) - Exécutons la commande pour installer les paquets nécessaires suivants :

```bash
sudo apt-get install apt-transport-https ca-certificates curl gnupg2 software-properties-common
```

C) - Vérifiez que l'installation a réussi en exécutant l'image hello-world :

```bash
La prochaine étape est d'ajouter le référentiel officiel de Docker à la machine
virtuelle Debian 11 pour récupérer les sources d'installation, en commençant par
obtenir la clé GPG pour assurer l'intégrité et l'authenticité des images Docker.
```

D) - Nous allons intégrer le référentiel Docker à la machine virtuelle Debian 11.

```bash
sudo echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-
archive-keyring.gpg] https://download.docker.com/linux/debian $
(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list
```

E) - Après avoir installé ces paquets, il est nécessaire d'exécuter la commande pour
mettre à jour la cache des paquets.

```bash
sudo apt-get update
```

F) - Enfin, nous exécutons la commande pour installer Docker.

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

G) - Pour vérifier si Docker a été correctement installé, vous exécutez une commande
pour vérifier l'état de Docker. La commande est la suivante :

```bash
sudo systemctl status docker
```

H) - Pour vérifier la version de Docker installée, vous pouvez le faire en utilisant la
commande suivante :

```bash
docker version
```

## **2 - Installation de Kubernetes:**

1 - Installer avec Homebrew sur macOS:

```bash
brew install kubectl
ou
brew install kubernetes-cli
```

- Testez pour vous assurer que la version que vous avez installée est à jour :

```bash
kubectl version --client
```
2 - Installer sur Linux (Debian-Ubuntu):

*Mise à jour et installation des dépendances :*

```bash
sudo apt update
sudo apt -y upgrade
sudo apt -y install curl apt-transport-https
```

*Ajouter la clé GPG et le dépôt Kubernetes :

```bash
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo apt update
```

*Installer kubelet, kubeadm et kubectl:*

```bash
sudo apt -y install vim git curl wget kubelet kubeadm kubectl
sudo apt-mark hold kubelet kubeadm kubectl
```
Cette commande installe les trois composants principaux :
- `kubelet` : Agent pour exécuter les pods.
- `kubeadm` : Outil pour initialiser un cluster Kubernetes.
- `kubectl` : Outil de ligne de commande pour gérer Kubernetes.

## **3 - Installation de Minikube:**
```bash
brew uninstall minikube
```
- Désinstaller Minikube:

```bash 
brew uninstall minikube
```
Pour définir le --driver avec minikube start, entrez le nom de l'hyperviseur que vous avez installé en minuscules: 

```bash
minikube start --driver=docker
```
<img width="783" alt="Screenshot 2025-01-16 alle 14 46 08" src="https://github.com/user-attachments/assets/f6afabf1-85c3-4b7b-a589-9af424c7a0c3" />

- Une fois minikube start terminé, exécutez la commande ci-dessous pour vérifier l'état du cluster :

```bash
minikube status
```
<img width="201" alt="Screenshot 2025-01-16 alle 14 48 20" src="https://github.com/user-attachments/assets/a2010245-5aa2-424a-ac4f-5a054a1048f0" />

NB. Pour que Minikube fonctionne avec Docker comme driver, il est nécessaire que Docker soit en cours d'exécution (en start).

---
### **1. Créer Namespace**

Il y a deux méthodes pour créer un espace de noms, et elles sont les suivantes :

1°: Avec le fichier yaml

```yaml
apiVersion: v1
kind: Namespace
metadata:
   name: development
```
```bash
kubectl apply -f namespace.yaml
```

2°: Vous pouvez créer un espace de noms directement depuis la ligne de commande en utilisant la commande `kubectl`:

```bash
kubectk create namespace development
```
```bash
kubectl create namespace NOME_NAMESPACE
```








