---
copyright:
  years: 2016,2018
lastupdated: "2018-06-12"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Architecture 
{: #architecture}

## Réplication

Un service {{site.data.keyword.composeForPostgreSQL_full}} se compose d'un cluster avec deux membres de données, un membre principal et un membre suiveur. Les données sont répliquées entre les membres de données et leur espace disque est réparti dans les zones de disponibilité de la région.  La haute disponibilité est gérée avec Patroni, où trois arbitres etcd assurent la maintenance de l'état du cluster et gèrent la réplication ainsi que le basculement. Lorsqu'un membre de données n'est plus accessible, votre cluster continue à fonctionner normalement.

## Chiffrement de disque

Tous les services {{site.data.keyword.composeForPostgreSQL}} disposent du chiffrement au repos. Vos données résident sur des serveurs où le chiffrement au niveau volume est activé. 

Etant donné que {{site.data.keyword.composeForPostgreSQL}} est un service géré, les opérateurs {{site.data.keyword.cloud}} Compose peuvent voir les données. Outre le chiffrement du disque, il est recommandé de chiffrer vos informations personnelles avant de les stocker dans la base de données ou d'utiliser des extensions ou des fonctions permettant d'activer le chiffrement sur la base de données elle-même. Même si ces méthodes risquent d'avoir un impact sur la facilité d'utilisation ou les performances, il est conseillé de s'assurer que les informations personnelles sont protégées par un chiffrement.

## Mise à l'échelle automatique

Les ressources sont automatiquement mises à l'échelle en fonction de l'utilisation totale du stockage sur disque des bases de données PostgreSQL. La mémoire est basée sur un rapport d'espace disque mis à disposition de 1 sur 4. Ces ressources sont intégrées en tant qu'unités.

La mise à l'échelle automatique est conçue pour répondre aux tendances à court et moyen termes de votre base de données. Votre service est contrôlé toutes les heures et, s'il est à court d'espace disque, des unités supplémentaires sont attribuées au déploiement. 

Une mise à l'échelle automatique ne réduit pas la taille des déploiements où l'utilisation du disque/de la mémoire à diminué. Les ressources mises à disposition de vos bases de données sont conservées pour les besoins ultérieurs ou jusqu'à ce que vous réduisiez manuellement votre déploiement.
{: .tip}

## Rôles

Chaque service PostgreSQL est mis à disposition avec un rôle "admin". D'autres rôles et droits d'accès peuvent être ajoutés et gérés via psql. Il n'existe pas de rôle "superutilisateur" pour ce service.

## Extensions de base de données

Utilisez psql pour lister, installer et gérer des extensions PostgreSQL.

Vous devez utiliser le rôle "admin" fourni pour exécuter les commandes CREATE et ALTER. {: .tip}

### Liste des extensions

Utilisez pg_available_extensions pour afficher la liste complète des extensions prises en charge.
`SELECT name FROM pg_available_extensions;`

### Installation d'extensions

Utilisez CREATE extension pour installer une extension.
`CREATE extension <name> ;`

### Mise à jour des extensions

Utilisez ALTER EXTENSION pour installer une nouvelle version d'une extension.
`ALTER EXTENSION <name> UPDATE TO <version>;`
