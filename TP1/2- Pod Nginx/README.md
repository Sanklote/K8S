# Pod Nginx

On on crée 'nginx-pod.yaml'
```bash
mkdir pod-nginx
nano nginx-pod.yaml
```
Le fichier 'nginx-pod.yaml' :
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  labels:
    app: nginx
spec:
  containers:
  - name: nginx
    image: nginx:latest
    ports:
    - containerPort: 80
```

On déploie le pod 
```bash
kubectl apply -f nginx-pod.yaml
```

On utilise la commande 'kubectl port-forward'
```bash
kubectl port-forward pod/nginx-pod 8080:80
```

Aller sur http://localhost:8080 avec curl par exemple.
