# Projet Ansible2 - LAMP Ynov DevOps B3
  
### Tips   
Si vous avez des problèmes sur une command utilisez `ansible --help` et surtout aller voir la **documentation**. Elle est extremement exhaustive.

:raising_hand: Si vous avez des soucis n'hésitez pas à m'appeler. 
 
## Résumé

**Travail en groupe de 3 maximum.**

Cet exercice en mode projet doit permettre de : 

- Déployer une stack LAMP containeurisée
  - Pouvoir contrôler la stack via Ansible 
    - Status
    - Start/Stop/Restart
    - Build les Dockerfile nécessaire au déploiement de la stack
  - Web : 
    - Sur un serveur dédié à la partie Web 
    - 2 containers Apache/Nginx
    - Capacité de scalabité horizontale des containers Web
    - Container PHP séparé pour servir tous les containers Web
  - Database :
    - Container Mysql sur serveur séparé de la partie web
    - Persistence des données
  - ReverseProxy : 
    - En frontal devant les serveurs web
    - Load Balancing docker
    - Round Robin  

Une nomenclature précise et détaillé des serveurs/container est nécessaire.



### Rendu :
- Rapport Technique détaillé
  - Page de Garde
  - Sommaire
  - Introduction
    - Schéma d'infrastructure Haut Niveau
  - Partie Reverse Proxy
    - Schéma d'infrastructure Bas Niveau
  - Partie Web
    - Schéma d'infrastructure Bas Niveau
  - Partie Database
    - Schéma d'infrastructure Bas Niveau
  - Vidéo de démonstration 
  - Conclusion
  - Annexe 
  - Source

### Présentation :
- Minimum 5min - Maximum 10 min
- Slides de présentation claires et professionnelles
- Démo de déploiement
- Temps Questions/Réponses


------------------------------------------------------------------------------------------------------------------------------------------------

## Informations Techniques : 

L'exécution de ce Playbook automatisera donc les actions suivantes sur nos hôtes distants :

- Côté serveur web :
  - Installer les packages apache2, php et php-mysql
  - Déployer les sources de notre application dans notre serveur web distant
  - S'assurer que le service apache est bien démarré


- Côté serveur base de données :
  - Installer les packages mysql
  - Modifier le mot de passe root
  - Autoriser notre serveur web à communiquer avec la base de données
  - Configurer notre table mysql avec les bonnes colonnes et autorisations

Fichier variable pour base de données : 
```
mysql_user: "admin"
mysql_password: "secret"
mysql_dbname: "blog"
db_host: XXX.XXX.XXX.XXX
webserver_host: XXX.XXX.XXX.XXX
```

- mysql_user : l'utilisateur de notre base de données mysql qui exécutera nos requêtes SQL depuis notre application web.
- mysql_password : le mot de passe de l'utilisateur de notre base de données mysql.
- mysql_dbname : le nom de notre base de données.
- db_host : l'ip de notre machine mysql (utile pour la partie configuration mysql de notre application web).
- webserver_host : l'ip de la machine web (utile pour autoriser uniquement l'ip du serveur web à communiquer avec notre base de données).


