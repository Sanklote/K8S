Faire les dockerfiles

```yml
FROM nginx:latest
COPY ./index.html /usr/share/nginx/html/index.html
```

publier
```bash
docker build -t <dockerhub-username>/monbonlait .
docker push <dockerhub-username>/monbonlait

docker build -t <dockerhub-username>/mesbonslegumes .
docker push <dockerhub-username>/mesbonslegumes

docker build -t <dockerhub-username>/mesbonslegumes-bio .
docker push <dockerhub-username>/mesbonslegumes-bio
```
