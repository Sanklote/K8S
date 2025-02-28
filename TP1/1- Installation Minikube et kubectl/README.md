# Installation de Minikube et Kubectl

### Instalation de Minikube 

Lien de la documentation : https://minikube.sigs.k8s.io/docs/start/?arch=%2Flinux%2Fx86-64%2Fstable%2Fdebian+package

On installe le lien fourni par les informations 
Pour ma part :
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
sudo dpkg -i minikube_latest_amd64.deb
```

On start minikube 
```bash
minikube start
```
Minicube s'utilise avec docker 

On est maintenant capable de taper cette commande pour vérifier que tout est bien installé.
```bash
minikube kubectl -- get po -A
```

On peut créér un alias
```bash
alias kubectl="minikube kubectl --"
```
On a plus qu'a taper cela.
```bash
kubectl get po -A
```

On lance un dashbord et on on connecte avec le lien qui nous ai donné à la fin 
```bash
minikube dashboard
```
