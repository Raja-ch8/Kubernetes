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

- Installer avec Homebrew sur macOS:

```bash
brew install kubectl
ou
brew install kubernetes-cli
```

- Testez pour vous assurer que la version que vous avez installée est à jour :

```bash
kubectl version --client
```
- Installer kubectl sur Linux :

```bash

```

