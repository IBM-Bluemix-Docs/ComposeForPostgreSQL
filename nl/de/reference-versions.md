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

# Versionen
{: #versions}

Bereitstellbare Versionen | Bevorzugte Version
----------|-----------
9.4.15, 9.5.10, 9.6.6 | 9.4.15, 9.5.10, 9.6.6
{: caption="Tabelle 1. Versionen von {{site.data.keyword.composeForPostgreSQL}}" caption-side="top"}

## Bevorzugte Version

Die bevorzugte Version ist normalerweise die neueste Version der PostgreSQL-Datenbank, die für {{site.data.keyword.composeForPostgreSQL}} verfügbar ist. Standardmäßig wird diese Version in der Dropdown-Liste des Versionsselektors auf der Katalogseite angezeigt. Außerdem wird die bevorzugte Version automatisch von der API bereitgestellt, sofern der Aufruf keine Versionsangabe beinhaltet.

### Protokoll für neue bevorzugte Versionen

Wenn eine neue Version zur Verfügung gestellt wird, so wird ihre Veröffentlichung angekündigt und die Version ist für die Bereitstellung verfügbar. Im Anschluss an die Veröffentlichung gibt es ein Zeitfenster mit einer Dauer von ungefähr 7 Tagen, in dem die neueste Version zwar bereits verfügbar ist, aber noch nicht als bevorzugte Version gilt. Dieses Zeitfenster ermöglicht den Benutzern, die Version bereitzustellen und zu testen, während ihnen die aktuelle Version weiterhin zur Verfügung steht. Außerdem erhalten Compose-Entwickler hierdurch die Möglichkeit, alle Probleme, die gegebenenfalls in der neuen Version auftreten, zu erkennen und zu beheben. Am Ende des 7-tägigen Zeitfensters wird die neue Version als bevorzugte Version definiert oder es wird ein neues Datum für diese Änderung angekündigt.

Die Liste der für die Bereitstellung verfügbaren Versionen finden Sie auf der {{site.data.keyword.composeForPostgreSQL}} [-Katalogseite](https://console.{DomainName}/catalog/services/compose-for-postgresql).

Eine aktuelle Liste der für Ihren {{site.data.keyword.composeForPostgreSQL}}-Service verfügbaren Versionen können Sie über den Endpunkt [GET /2016-07/deployments/:id/versions](https://apidocs.compose.com/v1.0/reference#2016-07-get-deployments-versions) abrufen.
