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

## Creazione di un backup su richiesta

Come per i backup pianificati puoi creare un backup manualmente. Per creare un backup manuale, passa alla pagina *Manage* del tuo dashboard del servizio e fai clic su *Backup now*.

## Scaricamento di un backup

Per scaricare un backup, passa alla pagina *Manage* del tuo dashboard del servizio e fai clic su *Download* nella riga corrispondente del backup che desideri scaricare.

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

Per ripristinare un backup in una nuova istanza, segui le istruzioni per visualizzare i backup esistenti, quindi fai clic sulla riga corrispondente per espandere le opzioni del backup che desideri scaricare. Fai clic sul pulsante **Restore**. Viene visualizzato un messaggio per farti sapere che è stato avviato un ripristino. La nuova istanza del servizio sarà automaticamente denominata "postgres-restore-[timestamp]" e visualizzata nel tuo dashboard dopo l'avvio del provisioning.
