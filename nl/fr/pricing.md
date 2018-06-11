---

copyright:
  years: 2016,2018
lastupdated: "2018-01-03"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Tarification
{: #pricing}

## Configuration de base
Un service {{site.data.keyword.composeForPostgreSQL_full}} démarre avec un cluster de deux noeuds de données, dotés chacun de 1 Go de mémoire et de 102 Mo de stockage, ce qui équivaut à 1 unité de ressources. Le service _inclut_ la réplication et la haute disponibilité, de sorte que chaque unité et le prix unitaire _incluent_ le coût des ressources dans les deux noeuds.

La configuration de base inclut également trois capsules etcd arbiter pour la gestion de la réplication, et deux capsules HAProxy pour la gestion des connexions et de la reprise en ligne. Les capsules HAProxy disposent chacune de 64 Mo de mémoire.

### Coût
Le prix de la configuration du service de base est défini. Consultez les vignettes du catalogue sur {{site.data.keyword.cloud_notm}} pour connaître la tarification de base dans votre devise locale. Par exemple, le prix de base en dollars US est de 12 $/mois.

## Options d'extension
Si vous avez besoin de davantage de mémoire ou de stockage pour votre service, vous pouvez augmenter les ressources allouées selon un rapport de 10 pour 1 en stockage sur disque et unité de mémoire. L'augmentation du disque alloué au déploiement augmente également la quantité de mémoire RAM allouée. Une unité {{site.data.keyword.composeForPostgreSQL}} se compose de 1 Go de stockage et de 102 Mo de mémoire, de sorte que chaque unité et le prix unitaire _incluent_ le coût d'accroissement des ressources dans les deux noeuds de données.

### Coût
Chaque unité supplémentaire (1 Go de stockage et 102 Mo de mémoire) a un prix unitaire indiqué dans votre devise locale dans la vignette du catalogue {{site.data.keyword.cloud_notm}} du service. En dollars US, chaque unité supplémentaire coûte 12 $. Le prix unitaire diminue proportionnellement à l'augmentation de la taille _totale_ de vos services {{site.data.keyword.composeForPostgreSQL}}, selon le barème indiqué dans le tableau de tarification différenciée ci-dessous.

### Tarification différenciée
Nombre d'unités|Prix unitaire
----------|-----------
1 - 9 unités|Prix unitaire de base -- soit 12,00 USD/unité
10 - 24 unités|10 % de réduction -- soit 10,80 USD/unité
25 - 49 unités|20 % de réduction -- soit 9,60 USD/unité
50 - 99 unités|30 % de réduction -- soit 8,40 USD/unité
100 - 499 unités|40 % de réduction -- soit 7,20 USD/unité
500 - 999 unités|50 % de réduction -- soit 6,00 USD/unité
1000 - 4999 unités|60 % de réduction -- soit 4,80 USD/unité
5000 unités et plus|70 % de réduction -- soit 3,60 USD/unité
{: caption="Tableau 1. Tarification différenciée pour {{site.data.keyword.composeForPostgreSQL}}" caption-side="top"}
