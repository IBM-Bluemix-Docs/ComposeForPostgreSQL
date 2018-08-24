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

# Architettura 
{: #architecture}

## Replica

Un servizio {{site.data.keyword.composeForPostgreSQL_full}} contiene un cluster con due membri dei dati; un membro leader e un follower. I dati vengono replicati su entrambi i membri dei dati e il loro spazio disco viene distribuito nelle zone di disponibilità della regione.  L'alta disponibilità viene gestita con Patroni, dove tre etcd arbiter conservano lo stato del cluster, gestiscono la replica e il failover. Se un membro dei dati diventa non raggiungibile, il cluster continuerà a funzionare normalmente.

## Crittografia del disco

Tutti i servizi {{site.data.keyword.composeForPostgreSQL}} hanno la crittografia a riposo. I tuoi dati si trovano su server che hanno la crittografia a livello di volume abilitata. 

Poiché questo {{site.data.keyword.composeForPostgreSQL}} è un servizio gestito, è possibile agli operatori {{site.data.keyword.cloud}} Compose di visualizzare i dati. In aggiunta alla crittografia del disco, ti consigliamo di codificare le informazioni personali prima di archiviarle nel database o di utilizzare le estensioni o le funzioni per abilitare la crittografia nel database stesso. Anche se questi metodi possono influire sull'usabilità o sulle prestazioni, è buona norma assicurarsi che le informazioni personali siano protette con la crittografia.

## Scalabilità automatica

Le risorse vengono ridimensionate automaticamente in base all'utilizzo della memoria disco totale dei database PostgreSQL. La memoria è basata su un rapporto di spazio disco di cui viene eseguito il provisioning di 1:4. Queste risorse sono raccolte in bundle come unità.

Il ridimensionamento automatico è progettato per rispondere alle tendenze a medio e a lungo termine del tuo database. Il tuo servizio viene controllato ogni ora e, se sta esaurendo lo spazio su disco, delle ulteriori unità vengono assegnate alla distribuzione. 

Il ridimensionamento automatico non riduce le distribuzioni in cui l'utilizzo di disco/memoria si è ridotto. Le risorse di cui è stato eseguito il provisioning ai tuoi database rimarranno per le tue future esigenze oppure finché non riduci manualmente la tua distribuzione.
{: .tip}

## Ruoli

Viene eseguito il provisioning di ogni servizio PostgreSQL con un ruolo "ammin". Possono essere aggiunti e gestiti altri ruoli o autorizzazioni tramite psql. Non esiste un ruolo "superuser" per questo servizio.

## Estensioni database

Utilizza psql per elencare, installare e gestire le estensioni PostgreSQL.

Devi utilizzare il ruolo "ammin" fornito per eseguire i comandi CREATE e ALTER. {: .tip}

### Elenco delle estensioni

Utilizza pg_available_extensions per ottenere un elenco completo di estensioni supportate.
`SELECT name FROM pg_available_extensions;`

### Installazione delle estensioni

Utilizza l'estensione CREATE per installare ogni estensione.
`CREATE extension <name> ;`

### Aggiornamento delle estensioni

Utilizza ALTER EXTENSION per installare una nuova versione di un'estensione.
`ALTER EXTENSION <name> UPDATE TO <version>;`
