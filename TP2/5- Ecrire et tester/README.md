deployment
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
        image: <dockerhub-username>/monbonlait
        ports:
        - containerPort: 80
```

service
```yaml
apiVersion: v1
kind: Service
metadata:
  name: serv-lait
spec:
  selector:
    app: monbonlait
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
```

ingress
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
              name: serv-lait
              port:
                number: 80
    - host: mesbonslegumes.fr
      http:
        paths:
        - pathType: Prefix
          path: "/"
          backend:
            service:
              name: serv-legumes
              port:
                number: 80
    - host: mesbonslegumes.fr/bio
      http:
        paths:
        - pathType: Prefix
          path: "/bio"
          backend:
            service:
              name: serv-legumes-bio
              port:
                number: 80
```