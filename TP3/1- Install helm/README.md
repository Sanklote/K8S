Se mettre dans le dossier temporaire 
```bash
cd tmp
```

Helm pour linux amd64 x86_64
```bash
git clone https://get.helm.sh/helm-v3.17.2-linux-amd64.tar.gz
```

décompresser
```bash
tar -zxvf helm-v3.17.2-linux-amd64.tar.gz
```

Déplacer les binaires
```bash
mv linux-amd64/helm /usr/local/bin/helm
```

Vérifier l'installation
```bash
helm help```
```
ou
```bash
helm version
```

