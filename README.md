# Projet Client-serveur
## Introduction

Pour cette partie de la réalisation du projet, nous avions comme objectif de réaliser un pipeline. Le processus devait nous permettre de récupérer une image, la traiter et la restituer sous forme de .exe. Nous avons tout d’abord réalisé le pipeline en local sur notre IDE afin de bien identifier toutes les étapes. Cette première approche était primordiale avant de s’attaquer à la partie cloud. Nous avons ensuite intégré notre pipeline au cloud d’Amazon AWS. Nous avons utilisé les lambdas et S3 pour la partie traitement de l’image et récupération des informations du document, puis GitHub Actions pour la partie création de l’exécutable.
Bien que ces missions nous semblassent simples au premier abord, nous nous sommes vite rendu compte de la complexité du cloud. Aujourd’hui, nous sommes à mi-parcours de la réalisation du projet. Nous avons maintenant comme objectif de commencer la partie automatisation par l’intelligence artificielle.

 ![shema pipeline](https://github.com/solenemorais/projetjs/blob/main/Capture%20d%E2%80%99e%CC%81cran%202021-01-28%20a%CC%80%2014.52.46.png)
### AWS  
Afin de pouvoir déployer rapidement cette solution tout en gardant le contrôle. Nous avons choisi de faire appel à une **solution de cloud-computing avec AWS** notamment. Nous avons conteneurisé les différentes fonctionnalités de notre programme. Pour cela, nous avons utilisé les modules « **Lambda** » pour implémenter les fonctions, des module « **S3** » pour stocker les documents xlsx reçu et les xlsx après correction puis un module « DynamoDB » ou « RDS » pour la base de données qui sera à implémenter dans le futur. 
L’avantage de cette architecture est de pouvoir isoler les fonctionnalités afin de les améliorer sans impacter le reste du processus. 
Cela permet aussi d’augmenter le nombre de fonctionnalités en venant simplement rajouter un module. 

#### EC2 - marie
Amazon Elastic Compute Cloud ou EC2 est un service proposé par Amazon permettant à des tiers de louer des serveurs sur lesquels exécuter leurs propres applications web. EC2 permet un déploiement extensible des applications en fournissant une interface web par laquelle un client peut créer des machines virtuelles, c'est-à-dire des instances du serveur, sur lesquelles le client peut charger n'importe quel logiciel de son choix.  
Même si EC2 est un service de serveurs cloud **rapides et fiables**, un service **scalable**, et **facile à gerer** ; nous avons préféré utiliser le service S3 qui est également **scalable et fiable** mais qui prend beaucoup **moins d’espace et qui est moins cher**.

#### Lambda. 
AWS Lambda est un service informatique qui exécute du code en réponse à des événements et gère automatiquement les ressources informatiques requises par ce code. 
Les avantages que l’on peut retenir de ce service sont les suivants :

•	AWS Lambda gère toute l’infrastructure pour exécuter notre code. En plus d’être “server-less”, c’est-à-dire que nous n’avons pas à gérer de serveurs et que le code est exécuté automatiquement, ce service s’occupe du redimensionnement et de l’ajout de nouveaux serveurs lorsque l’application s’accroît.  
•	AWS Lambda est peu coûteux pour une petite application, voire gratuit, lorsqu’on est en période d’essai. Les frais s’appliquent toutes les 100 ms d’exécution du code et selon le nombre de fois où il est déclenché. Ainsi, nous ne payons rien lorsque le code n'est pas exécuté.

S3 et Lambda nous sont grandement utiles pour le traitement de fichier en temps réel.
On peut utiliser Amazon S3 pour déclencher AWS Lambda afin que les données soient immédiatement traitées après leur chargement. (Voir schéma ci-dessous)

 ![shema lambda](https://github.com/solenemorais/projetjs/blob/main/Capture%20d%E2%80%99e%CC%81cran%202021-01-28%20a%CC%80%2014.41.10.png)
#### Bucket - solene
c'est une poche mais en anglais

### GitHub Actions - theo
GitHub actions nous permet d’automatiser les commandes Shell du pyinstaller qui sert à créer l’exécutable de notre application. 
Nous l’utilisons pour récupérer un fichier json dans un S3 AWS, puis pour lancer l’exécution du pyinstaller et enfin pour envoyer le .exe dans un nouveau bucket S3.

![github_action](https://github.com/solenemorais/projetjs/blob/main/github_action.png)
## Rétrospective projet - solene
