---

copyright:
  years: 2017,2018
lastupdated: "2017-06-07"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Connexion d'une application externe
{: #connecting-external-app}

Deux moyens permettent de connecter une application externe à {{site.data.keyword.composeForPostgreSQL_full}} :

- Une **chaîne de connexion**, qui peut être utilisée par certaines bibliothèques client et qui contient toutes les informations requises pour la connexion d'autres bibliothèques.

- Une **ligne de commande**, qui est une commande préformatée qui appellera `psql` avec les paramètres appropriés.

Les deux sont disponibles sur la page *Vue d'ensemble* du service {{site.data.keyword.composeForPostgreSQL}}.

## Connexion avec un pilote de langage

Postgres dispose d'un vaste éventail de pilotes de langage.  Le tableau en répertorie quelques uns des plus courants.

Langage|Exemples
----------|-----------
PHP|[pgsql](http://php.net/manual/en/pgsql.examples-basic.php)
Ruby|[ruby-pg](https://bitbucket.org/ged/ruby-pg/wiki/Home)
Ruby on Rails|[Rails guide](http://edgeguides.rubyonrails.org/configuring.html#configuring-a-postgresql-database)
Python|[Psycopg2](https://wiki.postgresql.org/wiki/Psycopg2_Tutorial)
C#|[ODBC](https://wiki.postgresql.org/wiki/Using_Microsoft_.NET_with_the_PostgreSQL_Database_Server_via_ODBC)
Go|[pq](https://godoc.org/github.com/lib/pq)
Node|[node-postgres](https://github.com/brianc/node-postgres/wiki/Example)

## Connexion avec la ligne de commande

**psql** est l'outil de ligne de commande pour se connecter à Postgres. Pour l'utiliser, les outils du client PostgreSQL doivent être installés sur le système local. Ils peuvent être installés via l'installation du package PostgreSQL complet téléchargé depuis postgresql.org, depuis vos packages de système d'exploitation ou sur MacOS X avec brew installé, en exécutant `brew install postgresql`).   

Pour plus d'informations sur psql, voir la documentation PostgreSQL ([reference](https://www.postgresql.org/docs/current/static/app-psql.html)) et l'[introduction](http://postgresguide.com/utilities/psql.html) simple du guide Postgres.

Vous trouverez la commande de ligne de commande que vous devez utiliser dans le tableau de bord de votre instance {{site.data.keyword.composeForPostgreSQL}}, à partir de l'onglet Vue d'ensemble.

```
psql "sslmode=require host=bluemix-sandbox-dal-9-portal.6.dblayer.com port=24761 dbname=compose user=admin"
```

Lorsque vous entrez la commande, vous êtes invité à fournir le mot de passe, que vous trouverez dans les informations de la chaîne de connexion sur le même onglet ou dans les *données d'identification du service*.

## Connexion avec pgAdmin3

pgAdmin3 est un client d'interface graphique répandu pour PostgreSQL. Pour vous connecter avec pgAdmin3, procédez comme suit :

1. Téléchargez et installez la version de pgAdmin3 adaptée à votre système d'exploitation à partir de [https://www.pgadmin.org/](https://www.pgadmin.org/).
2. Exécutez pgAdmin3 et sélectionnez "Ajouter un serveur" dans la barre de menus pour créer un nouvelle connexion et ouvrir le panneau *New Server Registration*.

  ![Panneau New Server Registration dans pgAdmin3. Onglet Properties.](./images/pgadmin.png "Onglet des propriétés du panneau New Server Registration dans pgAdmin3.")

3. Renseignez les zones du panneau avec les informations de la page Vue d'ensemble de votre service {{site.data.keyword.composeForPostgreSQL}} :

  * **Name** : tout nom décrivant votre déploiement Postgres.  Pour simplifier, choisissez le même nom que celui utilisé dans Compose.
  * **Host** : issu de la partie host de votre chaîne de connexion.
  * **Port** : issu de la partie port de votre chaîne de connexion.
  * **Username** : nom de l'administrateur ou d'un utilisateur que vous avez créé.
  * **Password** : mot de passe de l'administrateur (figure dans la section des données d'identification) ou d'un utilisateur que vous avez créé.

4. Une fois les zones renseignées, sélectionnez l'onglet "SSL" :

  ![Panneau New Server Registration dans pgAdmin3. Onglet SSL.](./images/pgadmin_ssl.png "Onglet SSL du panneau New Server Registration dans pgAdmin3.")

5. Modifiez la zone SSL en "require".
6. Cliquez sur "OK" pour sauvegarder les paramètres de connexion et vous connecter à la base de données.
