push le helm chart dans github

générer un index.yaml

```bash
helm repo index ./ --url https://<your-github-pages-url>
```

ajouter un artifacthub-repo.yml au repository

```bash
nano artifacthub-repo.yml
```

```yml
name: "ecommerce-store"
description: "Helm chart for deploying e-commerce stores"
type: "chart"
version: "0.1.0"
```

se créer un compte sur Artifact Hub.
suivre la documentation et publier avec l'URL du repository