## Le Serverless

La nouvelle coqueluche

----

### Définition

- Ce n'est pas une nouvelle offre cloud, mais un concept d'architecture
- Délivrer de la valeur pour le métier rapidement et régulièrement

----

### Propriétés désirables

- Ephémère
  - La plateforme attends les requêtes et n’instancie que les fonctions a la demande, qui ne ”vivent” le temps délivrer le résultat
- Scalabilité dynamique
  - Résilience supportée nativement par la plateforme
- Gestion fine
  - Pay-per-use sur le cloud
- Piloté par événements

----

### Propriétés désirables

- Attention aux contraintes
  - Pas d'état
  - Vendor lock-in
  - Cold start
  - Pas de service long

----

### Architecture traditionnelle

![Image](https://martinfowler.com/articles/serverless/ps.svg)

----

### Séparons l'architecture

<img src="https://martinfowler.com/bliki/images/serverless/sketch.png" width="50%" />

----

### Architecture serverless

<img src="https://martinfowler.com/articles/serverless/sps.svg" width="75%" />

----

### Architecture

Traditionnelle

<img src="https://martinfowler.com/articles/serverless/cp.svg" width="75%" />

Serverless

<img src="https://martinfowler.com/articles/serverless/scp.svg" width="75%" />

----

### Function-as-a-Service

Déployer du code comme plus petite unité de valeur
- Ephémère : durée de vie de l'ordre de la requête
- Dynamique : scalabilité et résilience supportés par la plateforme
- Fine grained : modèle de coût par appel

----

### Function-as-a-Service

<img src="img/faas.png" width="50%" />

----

### Backend-as-a-Service

- APIs pour délivrer des applications rapidement sans se soucier de la scalabilité et de la résilience
- Basé principalement sur les offres PaaS des CSP
- Peut être des bases de données (DynamoDB), de l'authentification (auth0.io), du stockage objet (blob storage)

----

### Backend-as-a-Service

<img src="img/baas.png" width="80%" />

----

### Autoscaling

Contrairement au PaaS ou au IaaS, la scalabilité est automatique et basé sur des métriques techniques et fonctionnelles

----

### Scale to zero

Du point de vue de l'utilisateur, s'il n'y a pas d'utilisation de l'environnement, il n'y a pas de coût associé

----

### Du IaaS au FaaS

- Le IaaS apporte plus de flexibilité, plus de maitrise, permet de faire du "lift-and-shift", mais il faut s'occuper de la plomberie
- Le FaaS se focuse sur la valeur ajoutée et le Time-to-Market, mais apporte son lot de contraintes

----

### Agilité et DevOps

- Le Severless tire partie au maximum du DevOps et de l'Agilité
- Tire parti au maximum des capacités du cloud : auto-scaling, elasticité, fine grained, pay-per-call model...
- Support les architectures d'aujourd'hui : Cloud-native applications, 12 factors

----

### Contraintes

- Impacte les architectures : pas de gestion de données (stateless)
- La sécurité doit être embarquée dans les applications : shift de la sécurité périmétrique
- Test du code compliqué : déploiement du code sur la plateforme à chaque changement, mettre en place des techniques types TDD ou BDD
- Métrologie et monitoring complexe
- Attention au vendor lock-in
- Estimation du coût compliqué

----

### Cas d'usage

- Microservices
- Stream processing
- IoT / Event-driven-programming
- Batch / Taches planifiées
- Grid computing

----

### Architecture

<img src="https://d3ansictanv2wj.cloudfront.net/fig_2-51d839a1bfd30c8dd1a9f0e608cacfe9.png" width="80%" />