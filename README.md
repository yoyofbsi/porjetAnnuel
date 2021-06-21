# Hard'Taumate

Bienvenue sur la page d'accueil de notre projet de déploiement d'infrastructure HA sécurisé.

L'objectif de cette documentation est de de recenser les différentes parties importantes à maitriser pour un déploiement.

## Environnement compatible

  * Debian 10

## Logiciels utilisés

  * Heartbeat
  * HAProxy
  * Nginx
  * ProxySQL
  * Percona Server
  * Orchestrator
  * Fail2ban
  * Lynis


## Les fondamentaux

  * [Préparation pré-déploiement](https://github.com/yoyofbsi/projetAnnuel/blob/master/preparation_deploiement.md)

  * [Créer et éditer le fichier d'inventaire d'une infrastructure](https://github.com/yoyofbsi/projetAnnuel/blob/master/preparation_inventory.md)

  * [Créer et éditer le fichier de variables d'une infrastructure](ajouter un lien vers une page explicative)

  * [Utiliser un coffre fort de mot de passe (vault)](ajouter un lien vers une page explicative)

  * [Utiliser Ansible pour réaliser un déploiement]()


## Les fonctionnalités concernant le middleware 

  * [Créer des VirtualHosts Apache](ajouter un lien vers une page explicative) (Si possibilité de créer plusieurs sites à la volée)

## Front (Heartbeat + HAProxy)
  
  * Heartbeat est un logiciel permettant d'empêcher un SPOF en configurant à la volée une adresse IP virtuelle et en lançant HAProxy.
  * HAProxy est un logiciel qui sert de load-balancer pour les serveur Web. Il permet de repartir la charge, et de ne renvoyer que vers les serveurs actifs.

## Middle (Nginx + ProxySQL)

  * Nginx est un logiciel permettant d'hébérger un ou plusieurs serveurs Web.
  * ProxySQL permet de gérer la connexion entre les serveurs Web et les serveurs SQL. Il sert aussi de load-balancer et transfert les requêtes au bon serveur en fonction de l'état Read-Only (sur les serveurs SQL)

## Back (Percona-server + Orchestrator)

  * Percona-server est une base de données relationnelle.
  * Orchestrator permet de gérer automatiquement le failover d'une base de données.
