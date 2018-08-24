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

# Versioni
{: #versions}

Versioni distribuibili | Versione preferita
----------|-----------
9.4.15, 9.5.10, 9.6.6 | 9.4.15, 9.5.10, 9.6.6
{: caption="Tabella 1. Versioni di {{site.data.keyword.composeForPostgreSQL}}" caption-side="top"}

## Versione preferita

La versione preferita è di norma la versione più recente del database PostgreSQL disponibile per {{site.data.keyword.composeForPostgreSQL}}. È la versione che corrisponde al valore predefinito nel selettore della versione a discesa nella pagina del catalogo. È anche la versione di cui viene seguito automaticamente il provisioning dall'API se non viene specificata alcuna versione nella chiamata.

### Nuovo protocollo di versione preferito

Quando viene resa disponibile una nuova versione, il suo rilascio verrà annunciato e sarà disponibile per la distribuzione. Dopo la data di rilascio, c'è una finestra di circa 7 giorni in cui la versione più recente è disponibile ma non è la versione preferita. Questa finestra ti consente di distribuire e verificare la nuova versione continuando però a disporre della versione corrente. Consente inoltre agli ingegneri di Compose di individuare e risolvere gli eventuali problemi che potrebbero presentarsi nella nuova versione. Alla fine della finestra di 7 giorni, la nuova versione viene impostata come versione preferita oppure viene annunciata una nuova data per questa modifica.

L'elenco di versioni disponibili per il provisioning è disponibile nella {{site.data.keyword.composeForPostgreSQL}} [pagina di catalogo](https://console.{DomainName}/catalog/services/compose-for-postgresql).

Per ottenere un elenco corrente di versioni disponibili per il tuo servizio {{site.data.keyword.composeForPostgreSQL}} puoi utilizzare l'endpoint
[GET /2016-07/deployments/:id/versions](https://apidocs.compose.com/v1.0/reference#2016-07-get-deployments-versions).
