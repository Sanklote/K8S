On commence par chercherNextcloud sur Artifact Hub
```bash
helm search hub nextcloud
```
On a :
```
URL                                                     CHART VERSION   APP VERSION     DESCRIPTION
https://artifacthub.io/packages/helm/nextcloud/...      6.6.9           30.0.6          A file sharing server that puts the control and...
https://artifacthub.io/packages/helm/rock8s/nex...      4.5.9           latest          agile project management platform
https://artifacthub.io/packages/helm/cloudve/ne...      1.13.0          17.0.0          A file sharing server that puts the control and...
https://artifacthub.io/packages/helm/th-charts/...      0.2.0           31.0.0          Nextcloud server, a safe home for all your data
https://artifacthub.io/packages/helm/linogics/n...      22.0.0-v7       22.0.0          Nextcloud Helm Chart by linogics.io
https://artifacthub.io/packages/helm/qjoly/next...      3.5.13          26.0.2          A file sharing server that puts the control and...
https://artifacthub.io/packages/helm/groundhog2...      0.19.2          31.0.2-apache   A Helm chart for Nextcloud on Kubernetes
https://artifacthub.io/packages/helm/si-gitops/...      3.6.5           28.0.14         A file sharing server that puts the control and...
https://artifacthub.io/packages/helm/homeenterp...      0.6.0           22.0.0-apache   file server
https://artifacthub.io/packages/helm/aws-nextcl...      4.6.7           28.0.2          Fork from nextcloud community for aws-eks nlb c...
https://artifacthub.io/packages/helm/schichtel/...      0.1.10          0.6.12          A Helm chart for nextcloud's push_notify server
https://artifacthub.io/packages/helm/collabora-...      1.1.36          24.04.13.2.1    Collabora Online helm chart
https://artifacthub.io/packages/helm/glasskube/...      0.12.2          0.12.2          The Glasskube Operator is an open source Kubern...
```

On prend donc :
```bash
helm repo add nextcloud https://nextcloud.github.io/helm/
helm repo update
```

On installe nextcloud
```bash
helm install my-release nextcloud/nextcloud
```
```bash
kubectl get pods
```


