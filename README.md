# Projet Client-serveur
## Technologies utilisées

### AWS

#### EC2

#### Lambda
AWS Lambda est un service informatique qui exécute du code en réponse à des événements et gère automatiquement les ressources informatiques requises par ce code. 
Les avantages que l’on peut retenir de ce service sont les suivants:

AWS Lambda gère toute l’infrastructure pour exécuter notre code. En plus d’être “server-less”, c’est-à-dire que nous n’avons pas à gérer de serveurs et que le code est exécuté automatiquement, ce service s’occupe du redimensionnement et de l’ajout de nouveaux serveurs lorsque l’application s’accroît.
AWS Lambda est peu coûteux pour une petite application, voire gratuit, lorsqu’on est en période d’essai. Les frais s’appliquent toutes les 100 ms d’exécution du code et selon le nombre de fois où il est déclenché. Ainsi, nous ne payons rien lorsque le code n'est pas exécuté.

S3 et Lambda nous sont grandement utiles pour le traitement de fichier en temps réel.
On peut utiliser Amazon S3 pour déclencher AWS Lambda afin que les données soient immédiatement traitées après leur chargement. (voir schéma ci-dessous)

<img src="projetjs/Capture d’écran 2021-01-28 à 14.41.10.png"
     alt="shema image"
     style="float: left; margin-right: 10px;" />
Fig.3 :Traitement fichiers temps réel S3 et Lambda

#### Bucket


### GitHub Actions
GitHub Actions facilite l'automatisation des flux de travail logiciels, désormais avec CI / CD de classe mondiale. Créez, testez et déployez votre code directement depuis GitHub. Faites en sorte que les révisions de code, la gestion des succursales et le tri des problèmes fonctionnent comme vous le souhaitez.


## Rétrospective projet
