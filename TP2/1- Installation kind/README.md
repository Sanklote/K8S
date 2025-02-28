# Installation kind

Installation kind pour linux x86_64
```bash
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.27.0/kind-linux-amd64
```

```bash
chmod +x ./kind
```

```bash
sudo mv ./kind /usr/local/bin/kind
```

Pour voir si tout marche bien
```bash
kind create cluster
```
et
```bash
docker ps
```
