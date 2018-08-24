---

copyright:
  years: 2017,2018
lastupdated: "2018-03-02"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Backup
{: #backups}

Puoi creare e scaricare i backup dalla scheda _Backups_ della pagina _Manage_ del tuo dashboard del servizio. Sono disponibili backup giornalieri, settimanali, mensili e su richiesta. Vengono conservati in base alla seguente pianificazione:

Tipo di backup|Pianificazione conservazione
----------|-----------
Giornaliero|I backup giornalieri sono conservati per 7 giorni
Settimanale|I backup settimanali sono conservati per 4 settimane
Mensile|I backup mensili sono conservati per 3 mesi
Su richiesta|Il backup su richiesta viene conservato. Il backup conservato è sempre il più recente backup su richiesta.
{: caption="Tabella 1. Pianificazione conservazione backup" caption-side="top"}

Le politiche di conservazione e di pianificazione del backup sono fissate. Se hai bisogno di conservare più backup rispetto a quelli consentiti dalla pianificazione di conservazione, devi scaricare i backup e conservare gli archivi in base ai tuoi requisiti di business.

## Visualizzazione dei backup esistenti

I backup giornalieri del tuo database vengono automaticamente pianificati. Per visualizzare i tuoi backup esistenti, passa alla pagina *Manage* del tuo dashboard del servizio. 

  ![Backup](./images/postgres-backups-show.png "Un elenco di backup nel dashboard del servizio")

Fai clic sulla riga corrispondente per espandere le opzioni per ogni backup disponibile.

  ![Opzioni backup](./images/postgres-backups-options.png "Opzioni per il backup.") 

### Utilizzo dell'API per visualizzare i backup esistenti

Un elenco dei backup è disponibile nell'endpoint `GET /2016-07/deployments/:id/backups`. L'endpoint fondazione, con l'ID istanza di servizio e l'ID distribuzione sono entrambi visualizzati nella _Panoramica_ del servizio. Ad esempio: 
``` 
https://composebroker-dashboard-public.mybluemix.net/api/2016-07/instances/$INSTANCE_ID/deployments/$DEPLOYMENT_ID/backups
```  

## Creazione di un backup su richiesta

Come per i backup pianificati puoi creare un backup manualmente. Per creare un backup manuale, passa alla pagina *Manage* del tuo dashboard del servizio e fai clic su *Backup now*.

### Utilizzo dell'API per creare un backup

Invia una richiesta POST all'endpoint di backup per avviare un backup manuale: `POST /2016-07/deployments/:id/backups`. Restituisce immediatamente l'ID ricetta e le informazioni sul backup mentre è in esecuzione. Dovrai controllare l'endpoint dei backup per vedere se il backup è terminato e trovare il relativo backup_id prima di utilizzarlo. Utilizza `GET /2016-07/deployments/:id/backups/`.

## Scaricamento di un backup

Per scaricare un backup, passa alla pagina *Manage* del tuo dashboard del servizio e fai clic su *Download* nella riga corrispondente del backup che desideri scaricare.

### Utilizzo dell'API per scaricare un backup

Trova il backup da cui vuoi eseguire il ripristino nella pagina _Backups_ del tuo servizio e copia il backup_id oppure utilizza il `GET /2016-07/deployments/:id/backups` per trovare un backup e il relativo backup_id tramite l'API Compose. Utilizza quindi il backup_id per trovare le informazioni e un link di download per uno specifico backup: `GET /2016-07/deployments/:id/backups/:backup_id`.

## Contenuti del backup

I backup di {{site.data.keyword.composeForPostgreSQL}} utilizzano `pg_basebackup` nella tua istanza del servizio in esecuzione. Il backup crea una copia binaria dei file del cluster e include tutti i file nella directory dei dati e in tutti gli spazi tabelle. Il backup include inoltre il file WAL (write ahead log), che puoi utilizzare per ripristinare un database in un momento coperto dai dati WAL.

## Utilizzo di un backup con un database locale

Puoi utilizzare il tuo backup {{site.data.keyword.composeForPostgreSQL}} per eseguire una copia locale del tuo database. La struttura del file del backup consente che più backup siano archiviati nella stessa directory; alcuni dei livelli principali sono `data --> backup --> *datestamp*`. Nella directory contrassegnata con data/ora troverai l'istantanea e l'archivio WAL.

Per ripristinare in un database locale:

1. Scarica un backup
2. Il backup include un file README: `data/backup/*timestamp*/snapshot/README`. Apri il file README in un editor di testo.
3. Scarica e installa PostgreSQL localmente. Il file README indica la versione di PostgreSQL con cui dovrebbe essere eseguito il backup.
4. Segui le istruzioni nel file README per eseguire una copia locale del tuo database. Avvia il tuo PostgreSQL locale nella directory dell'istantanea con il comando `postgres -D conf`. Puoi quindi collegarti al database eseguendo `psql postgres -U focker`.

## Ripristino di un backup

Per ripristinare un backup in una nuova istanza del servizio, segui le istruzioni per visualizzare i backup esistenti, quindi fai clic sulla riga corrispondente per espandere le opzioni del backup che desideri scaricare. Fai clic sul pulsante **Restore**. Viene visualizzato un messaggio per farti sapere che è stato avviato un ripristino. La nuova istanza del servizio sarà automaticamente denominata "postgres-restore-[timestamp]" e visualizzata nel tuo dashboard dopo l'avvio del provisioning.

### Ripristino tramite la CLI {{site.data.keyword.cloud_notm}}

Utilizza la seguente procedura per ripristinare un backup da un servizio PostgreSQL in esecuzione a un nuovo servizio PostgreSQL utilizzando la CLI {{site.data.keyword.cloud_notm}}. 
1. Se ne hai bisogno, [scaricala e installala](https://console.bluemix.net/docs/cli/index.html#overview). 
2. Trova il backup da cui vuoi eseguire il ripristino nella pagina _Backups_ del tuo servizio e copia l'ID backup.  
  **In alternativa**  
  Usa `GET /2016-07/deployments/:id/backups` per trovare un backup e il suo ID tramite la API Compose. L'endpoint fondazione e l'ID istanza di servizio sono entrambi visualizzati nella _Panoramica_ del servizio. Ad esempio: 
  ``` 
  https://composebroker-dashboard-public.mybluemix.net/api/2016-07/instances/$INSTANCE_ID/deployments/$DEPLOYMENT_ID/backups
  ```  
  La risposta avrà un elenco di tutti i backup disponibili per tale istanza del servizio. Scegli il backup da cui vuoi eseguire il ripristino e copiane l'ID.

3. Accedi con l'account e le credenziali appropriati. `ibmcloud login` (oppure `ibmcloud login -help` per visualizzare tutte le opzioni di accesso).

4. Passa alla tua organizzazione e al tuo spazio: `ibmcloud target -o "$YOUR_ORG" -s "YOUR_SPACE"`

5. Usa il comando `service create` per eseguire il provisioning di un nuovo servizio e fornire il servizio di origine e lo specifico backup che stai ripristinando in un oggetto JSON. Ad esempio:
``` 
ibmcloud service create SERVICE PLAN SERVICE_INSTANCE_NAME -c '{"source_service_instance_id": "$SERVICE_INSTANCE_ID", "backup_id": "$BACKUP_ID" }'
```
  Il campo _SERVICE_ deve essere compose-for-postgresql e il campo _PLAN_ deve essere Standard o Enterprise, a seconda del tuo ambiente. _SERVICE\_INSTANCE\_NAME_ è dove inserisci il nome per il tuo nuovo servizio. _source\_service\_instance\_id_ è l'ID dell'istanza di servizio dell'origine del backup; può essere ottenuto eseguendo `ibmcloud cf service DISPLAY_NAME --guid`, dove _DISPLAY\_NAME_ è il nome del servizio PostgreSQL da cui proviene il backup. 
  
  Gli utenti Enterprise dovranno anche specificare nell'oggetto JSON il cluster nel quale eseguire la distribuzione con il parametro `"cluster_id": "$CLUSTER_ID"`.
  
### Migrazione a una nuova versione

Alcuni upgrade di versione principale non sono disponibili nella distribuzione in esecuzione attuale. Dovrai eseguire il provisioning di un nuovo servizio che sta eseguendo la versione di cui è stato eseguito l'upgrade e migrare quindi in essa i tuoi dati utilizzando un backup. Questo processo è lo stesso di un ripristino di un backup di cui sopra, con l'unica differenza che specificherai la versione alla quale desideri eseguire l'upgrade.

``` 
ibmcloud service create SERVICE PLAN SERVICE_INSTANCE_NAME -c '{"source_service_instance_id": "$SERVICE_INSTANCE_ID", "backup_id": ""$BACKUP_ID", "db_version":"$VERSION_NUMBER" }'
```

Ad esempio, il ripristino di una versione meno recente di un servizio {{site.data.keyword.composeForPostgreSQL}} a un nuovo servizio che esegue PostgreSQL 9.6.6 sarà simile a:
```
ibmcloud service create compose-for-postgresql Standard migrated_postgres -c '{ "source_service_instance_id": "0269e284-dcac-4618-89a7-f79e3f1cea6a", "backup_id":"5a96d8a7e16c090018884566", "db_version":"9.6.6"  }'
