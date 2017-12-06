---

copyright:
  years: 2017
lastupdated: "2017-06-07"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Connessione a un'applicazione esterna
{: #connecting-external-app}

Esistono due modi per collegare un'applicazione esterna a {{site.data.keyword.composeForPostgreSQL_full}}:

- Può essere utilizzata una **Stringa di connessione** in alcune librerie client che contiene tutte le informazioni necessarie per il collegamento di altre librerie.

- La **Riga di comando** è un comando pre-formattato che richiamerà `psql` con i parametri corretti. 

Troverai entrambe nella pagina *Overview* del tuo servizio {{site.data.keyword.composeForPostgreSQL}}.

## Connessione con un driver di linguaggio 

Postgres dispone di una grande array di driver di linguaggio.  La tabella comprende alcuni dei più comuni.

Linguaggio|Esempi
----------|-----------
PHP|[pgsql](http://php.net/manual/en/pgsql.examples-basic.php)
Ruby|[ruby-pg](https://bitbucket.org/ged/ruby-pg/wiki/Home)
Ruby on Rails|[Rails guide](http://edgeguides.rubyonrails.org/configuring.html#configuring-a-postgresql-database)
Python|[Psycopg2](https://wiki.postgresql.org/wiki/Psycopg2_Tutorial)
C#|[ODBC](https://wiki.postgresql.org/wiki/Using_Microsoft_.NET_with_the_PostgreSQL_Database_Server_via_ODBC)
Go|[pq](https://godoc.org/github.com/lib/pq)
Node|[node-postgres](https://github.com/brianc/node-postgres/wiki/Example)

## Connessione con la riga di comando 

**psql** è lo strumento della riga di comando per il collegamento a Postgres. Per utilizzarlo, gli strumenti del client PostgreSQL dovranno essere installati nel sistema locale. Possono essere installati tramite l'installazione completa del pacchetto PostgreSQL scaricato da postgresql.org, dai tuoi pacchetti dei sistemi operativi o su MacOS X con brew installato, esegui `brew install postgresql`).   

Puoi avere ulteriori informazioni su psql nella documentazione di PostgreSQL - [reference](https://www.postgresql.org/docs/current/static/app-psql.html) - e in [introduction](http://postgresguide.com/utilities/psql.html) nel manuale Postgres.

Puoi trovare il comando della riga di comando che devi utilizzare nel tuo dashboard dell'istanza {{site.data.keyword.composeForPostgreSQL}}, dalla scheda della panoramica.

```
psql "sslmode=require host=bluemix-sandbox-dal-9-portal.6.dblayer.com port=24761 dbname=compose user=admin"
```

Quando immetti il comando ti sarà richiesta la password, che puoi trovare nelle informazioni della stringa di connessione nella stessa scheda o in *Service credentials*.

## Connessione con pgAdmin3

pgAdmin3 è un client GUI popolare per PostgreSQL. Utilizza la seguente procedura per il collegamento con pgAdmin 3

1. Scarica e installa la versione di pgAdmin3 per il tuo sistema operativo da [https://www.pgadmin.org/](https://www.pgadmin.org/).
2. Esegui pgAdmin3 e seleziona "Add Server" dalla barra del menu per creare una nuova connessione per aprire il pannello *New Server Registration*.

  ![Il pannello della nuova registrazione server in pgAdmin3. Scheda delle proprietà.](./images/pgadmin.png "La scheda delle proprietà del pannello della nuova registrazione server in pgAdmin3.")

3. Completa i campi nel pannello con le informazioni nella tua pagina della panoramica del servizio {{site.data.keyword.composeForPostgreSQL}}:

  * **Name**: può essere qualsiasi cosa descriva la tua distribuzione Postgres.  Per semplicità, utilizza lo stesso nome utilizzato in Compose.
  * **Host**: questo sarà la parte dell'host della tua stringa di connessione.
  * **Port**: questo sarà la parte della porta della tua stringa di connessione. 
  * **Username**: questo sarà il nome utente di admin o di un utente che hai creato.
  * **Password**: questo sarà la password di admin (che si trova nella sezione delle credenziali) o di un utente che hai creato.

4. Dopo aver completato i campi, seleziona la scheda "SSL":

  ![Il pannello della nuova registrazione server in pgAdmin3. Scheda SSL.](./images/pgadmin_ssl.png "La scheda SSL del pannello della nuova registrazione server in pgAdmin3.")

5. Modifica SSL con "require".
6. Fai clic su "OK" per salvare le impostazioni di connessione e collegarti al database.
