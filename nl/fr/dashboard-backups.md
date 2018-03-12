---

copyright:
  years: 2017,2018
lastupdated: "2017-09-07"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Sauvegardes
{: #backups}

Vous pouvez créer et télécharger des sauvegardes à partir de l'onglet _Backups_ de la page _Gérer_ du tableau de bord de votre service. Vous avez le choix entre les sauvegardes quotidiennes, hebdomadaires, mensuelles et à la demande. Elles sont conservées selon la planification suivante :

Type de sauvegarde|Planification de conservation
----------|-----------
Quotidienne|Les sauvegardes quotidiennes sont conservées pendant 7 jours
Hebdomadaire|Les sauvegardes hebdomadaires sont conservées pendant 4 semaines
Mensuelle|Les sauvegardes mensuelles sont conservées pendant 3 mois
A la demande|Une seule sauvegarde à la demande est conservée. Il s'agit toujours de la dernière sauvegarde à la demande effectuée.
{: caption="Tableau 1. Planification de conservation des sauvegardes" caption-side="top"}

Les planifications de sauvegarde et les règles de conservation sont fixées. Si vous avez besoin de conserver davantage de sauvegardes que ne le permet la planification de conservation, vous devez télécharger les sauvegardes et les archiver en fonction de vos exigences métier.

## Affichage des sauvegardes existantes

Des sauvegardes quotidiennes de votre base de données sont automatiquement planifiées. Pour afficher vos sauvegardes existantes, accédez à la page *Gérer* du tableau de bord de votre service. 

![Sauvegardes](./images/postgres-backups-show.png "Liste des sauvegardes dans le tableau de bord du service")

Cliquez sur la ligne correspondante pour développer les options de chaque sauvegarde disponible.

![Options de sauvegarde](./images/postgres-backups-options.png "Options d'une sauvegarde.") 

## Création d'une sauvegarde à la demande

Outre les sauvegardes planifiées, vous pouvez créer une sauvegarde manuelle. Pour créer une sauvegarde manuelle, accédez à la page *Gérer* du tableau de bord de votre service et cliquez sur *Backup now*.

## Téléchargement d'une sauvegarde

Pour télécharger une sauvegarde, accédez à la page *Gérer* du tableau de bord de votre service et cliquez sur *Télécharger* sur la ligne correspondant à la sauvegarde que vous voulez télécharger.

## Contenu de sauvegarde

Les sauvegardes {{site.data.keyword.composeForPostgreSQL}} utilisent `pg_basebackup` sur votre instance de service en cours d'exécution. La sauvegarde effectue une copie binaire des fichiers de cluster et inclut tous les fichiers dans le répertoire de données et dans tous les espaces de table. La sauvegarde inclut également le fichier WAL (write ahead log), que vous pouvez utiliser pour restaurer une base de données à un point temporel couvert par les données WAL.

## Utilisation d'une sauvegarde avec une base de données locale

Vous pouvez utiliser votre sauvegarde {{site.data.keyword.composeForPostgreSQL}} pour exécuter une copie locale de votre base de données. La structure de fichier de la sauvegarde permet de stocker plusieurs sauvegardes dans le même répertoire ; les premiers niveaux supérieurs sont `data --> backup --> *datestamp*`. Le répertoire datestamped contient un Instantané de l'archive WAL.

Pour restaurer dans une base de données locale :

1. Téléchargez une sauvegarde.
2. La sauvegarde inclut un fichier README : `data/backup/*timestamp*/snapshot/README`. Ouvrez le fichier README dans un éditeur de texte.
3. Téléchargez et installez PostgreSQL en local. Le fichier README indique la version de PostgreSQL avec laquelle la sauvegarde doit s'exécuter.
4. Suivez les instructions du fichier README pour effectuer une copie locale de votre base de données. Démarrez votre version PostgreSQL locale dans le répertoire des instantanés avec la commande `postgres -D conf`. Vous pouvez ensuite vous connecter à la base de données en exécutant : `psql postgres -U focker`.

## Restauration d'une sauvegarde

Pour restaurer une sauvegarde sur une nouvelle instance de service, suivez la procédure d'affichage des sauvegardes, puis cliquez sur la ligne correspondante afin de développer les options de la sauvegarde que vous voulez télécharger. Cliquez sur le bouton **Restore**. Un message vous indiquant qu'une restauration a été initiée s'affiche. La nouvelle instance de service sera automatiquement nommée "postgres-restore-[timestamp]" ; elle s'affiche dans votre tableau de bord au démarrage de la mise à disposition.
