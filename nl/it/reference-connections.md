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

# Configurazione della connessione
{: #connection-configuration}

Le connessioni database {{site.data.keyword.composeForPostgreSQL_full}} sono gestite da 2 portali HAProxy. Ogni portale ha 64MB di memoria. L'utilizzo di due portali consente alle applicazioni di mantenere la connettività se uno dei due diventa irraggiungibile.

Il failover al lato client è responsabilità del progettista dell'applicazione. Alcuni driver PostgreSQL gestiscono più stringhe di connessione e il failover normale in modo automatico. A meno che tu non stia lavorando con un driver che gestisce completamente gli errori di failover, devi:

* Lavorare con un driver che accetta più endpoint nella sua configurazione della connessione.
* Assicurarti che le chiamate delle tue applicazioni per leggere o scrivere nel database reagiscano in modo appropriato agli errori. Le opzioni includono:
  + Registrazione dell'errore e riconnessione.
  + Riconnessione e nuovo tentativo dell'operazione che ha causato l'errore.
  + Accodamento dell'operazione non riuscita e pianificazione della riconnessione.

## Crittografia in transito

Tutti i portali HAProxy {{site.data.keyword.composeForPostgreSQL}} hanno TLS/SSL abilitati e supportano TLS versione 1.2. I certificati per il servizio sono certificati autofirmati. Potresti dover salvare una copia locale del certificato per il tuo servizio e fornirne l'ubicazione al driver della tua applicazione per creare una connessione sicura.

## Limiti connessioni

Le connessioni al database hanno un limite di connessione iniziale di 100 connessioni per il servizio. A seconda delle risorse che assegni al servizio tramite il ridimensionamento automatico o manuale, il limite di connessioni verrà portato a un massimo di 1000 connessioni. Il superamento del limite di connessione renderà il tuo servizio non rispondente.

Puoi gestire le connessioni dalla tua applicazione tramite la funzione di pooling di connessioni del tuo driver.
{: .tip}

## Timeout proxy

I portali HAProxy gestiscono il ciclo di vita delle connessioni tra il server e il client. Li descriviamo qui in dettaglio come guida di riferimento per gli scrittori di driver e per gli altri che hanno un interesse nell'attività di basso livello delle connessioni al database {{site.data.keyword.composeForPostgreSQL}}.

Impostazione | Valore | Applicazione
----------|-----------|-----------
client | 1 giorno | Quando si prevede che il client riconosca o invii i dati.
connect | 4s | Quando si sta stabilendo una connessione tra il proxy e il server.
server | 30m | Quando si prevede che il server riconosca o invii i dati.
tunnel | 1g | Quando viene stabilita una connessione bidirezionale tra un client e un server e la connessione rimane inattiva in entrambe le direzioni.
client-fin | 5m | Quando si prevede che il client riconosca o invii dati mentre una direzione è già stata arrestata.
check | 5s | Come un controllo di timeout secondario quando si sta stabilendo una connessione tra il proxy e il server.

{: caption="Tabella 1. Timeout PostgreSQL HAProxy" caption-side="top"}
