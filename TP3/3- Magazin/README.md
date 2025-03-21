```bash
helm create ecommerce-store
```


Création deployment monbonlait

```bash
nano monbonlait-deployment.yaml
```
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: monbonlait-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: monbonlait
  template:
    metadata:
      labels:
        app: monbonlait
    spec:
      containers:
      - name: monbonlait-container
        image: antssy17/monbonlait
        ports:
        - containerPort: 80
```

Création service monbonlait

```bash
nano monbonlait-service.yaml
```
```yaml
apiVersion: v1
kind: Service
metadata:
  name: monbonlait-service
spec:
  selector:
    app: monbonlait
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
```

Création deployment legume

```bash
nano legume-deployment.yaml
```
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: legume-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: legume
  template:
    metadata:
      labels:
        app: legume
    spec:
      containers:
      - name: legume-container
        image: antssy17/legume
        ports:
        - containerPort: 80
```

Création service legume

```bash
nano legume-service.yaml
```

```yaml
apiVersion: v1
kind: Service
metadata:
  name: legume-service
spec:
  selector:
    app: legume
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
```

Création deployment legumebio

```bash
nano legumebio-deployment.yaml
```
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: legumebio-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: legumebio
  template:
    metadata:
      labels:
        app: legumebio
    spec:
      containers:
      - name: legumebio-container
        image: antssy17/legumebio
        ports:
        - containerPort: 80
```

Création service legumebio

```bash
nano legumbio-service.yaml
```

```yaml
apiVersion: v1
kind: Service
metadata:
  name: legumebio-service
spec:
  selector:
    app: legumebio
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
```

```bash
nano ingress.yaml
```

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: ecommerce-ingress
spec:
  rules:
    - host: monbonlait.fr
      http:
        paths:
        - pathType: Prefix
          path: "/"
          backend:
            service:
              name: monbonlait-service
              port:
                number: 80
    - host: mesbonslegumes.fr
      http:
        paths:
        - pathType: Prefix
          path: "/"
          backend:
            service:
              name: legume-service
              port:
                number: 80
    - host: mesbonslegumes.fr/bio
      http:
        paths:
        - pathType: Prefix
          path: "/bio"
          backend:
            service:
              name: legumesbio-service
              port:
                number: 80
```

```bash
helm install monbonlait ./ecommerce-store --set ingress.host=monbonlait.fr,image.repository=antssy17/monbonlait,image.tag=latest,service.port=80,replicaCount=1
```

```bash
helm install mesbonslegumes ./ecommerce-store --set ingress.host=mesbonslegumes.fr,image.repository=antssy17/legume,image.tag=latest,service.port=80,replicaCount=1
```


```bash
helm install mesbonslegumes-bio ./ecommerce-store --set ingress.host=mesbonslegumes.fr,bio,image.repository=antssy17/legumebio,image.tag=latest,service.port=80,replicaCount=1,path=/bio
```
