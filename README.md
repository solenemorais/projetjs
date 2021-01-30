# <span class="underline">Projet Client-serveur</span> 
## <span class="underline">Introduction</span> 

Pour cette partie de la réalisation du projet, nous avions comme objectif de réaliser un pipeline.  Le processus devait nous permettre de récupérer une image, la traiter et la restituer sous forme de .exe.  Nous avons tout d’abord réalisé le pipeline en local sur notre IDE afin de bien identifier toutes les étapes. Cette première approche était primordiale avant de s’attaquer à la partie cloud.  Nous avons ensuite intégré notre pipeline au cloud d’Amazon AWS. Nous avons utilisé les lambdas et S3 pour la partie traitement de l’image et récupération des informations du document, puis GitHub Actions pour la partie création de l’exécutable.  Bien que ces missions nous semblassent simples au premier abord, nous nous sommes vite rendu compte de la complexité du cloud.  

 ![shema pipeline](https://github.com/solenemorais/projetjs/blob/main/Capture%20d%E2%80%99e%CC%81cran%202021-01-28%20a%CC%80%2014.52.46.png)
###   <span class="underline">AWS</span>
Afin de pouvoir déployer rapidement cette solution tout en gardant le contrôle. Nous avons choisi de faire appel à une **solution de cloud-computing avec AWS** notamment. Nous avons conteneurisé les différentes fonctionnalités de notre programme.

Pierre connait bien AWS et les fonctionnalités du service. Il avait déjà réalisé plusieurs projets grâce à AWS et était en mesure de nous expliquer le fonctionnement, la facturation et l'intérêt que représentait une solution comme celle-ci. Pour le projet, AWS était la solution : on allait pouvoir automatiser tout le projet simplement et proprement.

Pour cela, nous avons utilisé les modules « **Lambda** » pour implémenter les fonctions, des module « **S3** » pour stocker les documents xlsx reçu et les xlsx après correction puis un module « DynamoDB » ou « RDS » pour la base de données qui sera à implémenter dans le futur. 
L’avantage de cette architecture est de pouvoir isoler les fonctionnalités afin de les améliorer sans impacter le reste du processus. 
Cela permet aussi d’augmenter le nombre de fonctionnalités en venant simplement rajouter un module. 

#### <span class="underline">EC2</span>
Avant de se lancer dans une succession de lambda et de bucket, on connaissait l'existence de EC2 sur AWS. Amazon Elastic Compute Cloud est un service proposé par Amazon grâce auquel on aurait pu louer des serveurs et exécuter notre propre application web dessus. EC2 nous aurait permis de déployer notre application en fournissant une interface web. On aurait pu créer des machines virtuelle, c'est-à-dire des instances du serveur, sur lesquelles on aurait pu charger n'importe quel logiciel de notre choix.
EC2 est un service de serveurs cloud **rapides et fiables**, un service **scalable**, et **facile à gerer**.
A première vue EC2 semblait une solution idéale pour AvekIA et structurer l'application. Cependant, pour Pierre, il existait un autre moyen d'intégrer notre application au cloud AWS. Il nous a alors expliqué que notre projet était réalisable via le service S3 et les Lambda. Le service S3 et les lambdas, également **scalable et fiable**, nous permetterait de faire exactement la même chose que sur EC2 mais en prenant beaucoup moins d'espace et en nous coûtant moins cher. POur une start-up, il est important d'évaluer le prix des solutions et de toujours essayer de trouver le mieux et le moins cher.


#### <span class="underline">Lambda</span> 
AWS Lambda est un service informatique qui exécute du code en réponse à des événements et gère automatiquement les ressources informatiques requises par ce code. 
Les avantages que l’on peut retenir de ce service sont les suivants :

•	AWS Lambda gère toute l’infrastructure pour exécuter notre code. En plus d’être “server-less”, c’est-à-dire que nous n’avons pas à gérer de serveurs et que le code est exécuté automatiquement, ce service s’occupe du redimensionnement et de l’ajout de nouveaux serveurs lorsque l’application s’accroît.  
•	AWS Lambda est peu coûteux pour une petite application, voire gratuit, lorsqu’on est en période d’essai. Les frais s’appliquent toutes les 100 ms d’exécution du code et selon le nombre de fois où il est déclenché. Ainsi, nous ne payons rien lorsque le code n'est pas exécuté.

S3 et Lambda nous sont grandement utiles pour le traitement de fichier en temps réel.
On peut utiliser Amazon S3 pour déclencher AWS Lambda afin que les données soient immédiatement traitées après leur chargement. (Voir schéma ci-dessous)

![shema lambda](https://github.com/solenemorais/projetjs/blob/main/Capture%20d%E2%80%99e%CC%81cran%202021-01-28%20a%CC%80%2014.41.10.png)
#### Bucket
Amazon Simple Storage Service (Amazon S3) est un service de stockage d'objets offrant une évolutivité, une disponibilité des données, une sécurité et des performances de pointe. Les clients de toutes tailles et de tous secteurs peuvent ainsi utiliser ce service afin de stocker et protéger n'importe quelle quantité de données.  
Les avantages que l’on peut retenir de ce service sont les suivants:

- Ses performances  
- Sa scabilité  
- Sa disponibilité  
- Sa durabilité de pointe  
- Son stockage économique  
- Sa facilité à gérer les données et les contrôles d'accès  

Nous utilisons des buckets S3 dans notre projet afin de stocker différentes sortes de fichiers envoyés par nos Lambda qui sont des "déclencheurs". Ces bucket servent un peu d'intermédiaire entre nos Lambda et nous permettent de stocker les fichiers reçus et transformés. Par exemple, on aura un bucket S3 contenant les images de formulaire et un autre bucket contenant les json des positions des éléments de ces formulaires à la suite de l'exécution d'une Lambda.

### <span class="underline">GitHub Actions</span>
GitHub actions nous permet d’automatiser les commandes Shell du pyinstaller qui sert à créer l’exécutable de notre application. 
Nous l’utilisons pour récupérer un fichier json dans un S3 AWS, puis pour lancer l’exécution du pyinstaller et enfin pour envoyer le .exe dans un nouveau bucket S3.  
GitHub actions nous a permis de contourner un problème les Lambda qui ne sont pas adaptées pour effectuer les commandes shell utiles à la création de notre .exe. 

![github_action](https://github.com/solenemorais/projetjs/blob/main/github_action.png)
## <span class="underline">Rétrospective projet</span>

 Depuis le début de ce projet, nous avons appris beaucoup de chose que ce soit sur le plan technique ou sur le plan organisationnel.

 Nous avons été confrontés à plusieurs difficultés qui nous ont amenées à réfléchir, comprendre et trouver une solution. Nous avons compris qu’il fallait d’abord bien définir les étapes du projet ainsi que leur intérêt avant d’intégrer la pipeline à AWS. Un projet comme celui-ci nous a permis d’appliquer nos connaissances et d’approfondir les outils que nous avions déjà pu voir lors de notre scolarité. D’autre part, nous avons gagné en autonomie en nous forçant à d’abord chercher par nous même avant de demander de l’aide.
 
 Travailler pour une start-up comme AvekIA est stimulant. Nous développons sans cesse notre esprit d’équipe et avons un réel sentiment d’appartenance à la communauté AvekIA. Pierre et Aymeric sont très disponible pour répondre à nos questions et nous aider, ce qui représentait un réel atout. Nous avons découvert les avantages et libertés d’une structure plus petite. Nous n’avons pas peur d’exprimer nos idées ou de prendre des responsabilités. Nous sommes tout le temps en train de tester, analyser et remettre en question nos choix ce qui nous amène à sans cesse innover et ne jamais nous ennuyer.
 
 A mi-parcours du projet de fin d’études, nous pouvons dire que nous avons terminé toute la structure ce celui-ci. Nous avons rempli les objectifs à atteindre pour cette première partie et sommes prêt à attaquer la partie Intelligence Artificielle.
