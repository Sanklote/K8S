# Connexion entre plusieurs pods

Création de 'mysql-pod.yaml'

```bash
nano mysql-pod.yaml
```

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: mysql-pod
  labels:
    app: mysql
spec:
  containers:
  - name: mysql
    image: mysql:5.7
    env:
    - name: MYSQL_ROOT_PASSWORD
      value: "root"
    ports:
    - containerPort: 3306
```

Création de 'phpmyadmin-pod.yaml'

```bash
nano phpmyadmin-pod.yaml
```

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: phpmyadmin-pod
  labels:
    app: phpmyadmin
spec:
  containers:
  - name: phpmyadmin
    image: phpmyadmin/phpmyadmin
    ports:
    - containerPort: 80
    env:
    - name: PMA_HOST
      value: mysql
```

On déploie les pods
```bash 
kubectl apply -f mysql-pod.yaml
kubectl apply -f phpmyadmin-pod.yaml
```

On crée le fichier 'mysql-service.yaml'

```bash
nano mysql-service.yaml
```

```yaml
apiVersion: v1
kind: Service
metadata:
  name: mysql-service
spec:
  selector:
    app: mysql
  ports:
  - protocol: TCP
    port: 3306
    targetPort: 3306
```

On déploie 'mysql-service.yaml'
```bash
kubectl apply -f mysql-service.yaml
```

On modifie 'phpmyadmin-pod.yaml'
```bash
nano phpmyadmin-pod.yaml
```

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: phpmyadmin-pod
  labels:
    app: phpmyadmin
spec:
  containers:
  - name: phpmyadmin
    image: phpmyadmin/phpmyadmin
    ports:
    - containerPort: 80
    env:
    - name: PMA_HOST
      value: mysql-service
```

On applique : 
```bash
kubectl apply -f phpmyadmin-pod.yaml
```
 On redirige le port 8081 vers le port 80 de phpmyadmin
```bash
kubectl port-forward pod/phpmyadmin-pod 8081:80
```

On accède avec http://localhost:8081 ou 
```bash
curl http://localhost:8081
```


