## Kubernetes

----

### Orchestrateur de containers

Afin de garantir qu'un container fonctionne, il est nécessaire d'avoir un orchestrateur de container

Celui-ci garanti que le container est toujours en fonctionnement, même si les noeuds du cluster se mettent à jour ou tombent en panne

----

### Docker Swarm

Docker Swarm est l'orchestrateur par défaut de Docker

Il est inclus dans le moteur et simple d'utilisation

Cependant, il ne répond pas à des contraintes de production

----

### Pods

Un pod est un regroupement de container au sein d'une même unité

<img src="https://d33wubrfki0l68.cloudfront.net/5cb72d407cbe2755e581b6de757e0d81760d5b86/a9df9/docs/tutorials/kubernetes-basics/public/images/module_03_nodes.svg" width="50%" />

----

### Horizontal pod autoscaler

Lorsqu'une demande est faite de scaler les pods, HPA s'occupe de démarrer les pods sur les noeuds correspondant, respectant les contraintes imposées

----

### Deployment

Un déploiement est la manière de déployer un pod

Un déploiement est déclaratif, c'est-à-dire que Kubernetes va s'assurer que les pods sont toujours au bon nombre demandés

<img src="https://d33wubrfki0l68.cloudfront.net/152c845f25df8e69dd24dd7b0836a289747e258a/4a1d2/docs/tutorials/kubernetes-basics/public/images/module_02_first_app.svg" width="30%" />

----

### Services

Un service est la manière d'accéder aux pods

Un service expose une adresse IP, ainsi qu'un port

Il joue le role de load-balancer

<img src="https://d33wubrfki0l68.cloudfront.net/cc38b0f3c0fd94e66495e3a4198f2096cdecd3d5/ace10/docs/tutorials/kubernetes-basics/public/images/module_04_services.svg" width="30%" />

----

### Ingress



----

### Cluster autoscaler

----

### Daemonset

----

### Storageclass

----

### Persistent volume

----

### Persistent volume claim

----

### Rolling update

----

### Healthcheck

----

### Logging

----

### Monitoring

----

### Alerting

----

### Architecture Kubernetes

----

### Offres managés cloud

----

### Helm

----

### Service Mesh