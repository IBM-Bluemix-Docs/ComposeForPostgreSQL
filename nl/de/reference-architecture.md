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

# Architektur 
{: #architecture}

## Replikation

Ein {{site.data.keyword.composeForPostgreSQL_full}}-Service enthält einen Cluster mit zwei Datenelementen (Membern), von denen ein Member als Leader und das andere als Follower fungiert. Die Daten werden über beide Datenelemente repliziert und ihr Plattenspeicherplatz wird auf die Verfügbarkeitszonen der Region verteilt.  Die Hochverfügbarkeit wird mit Patroni verwaltet, und zwar anhand von drei etcd-Arbitern, die den Clusterstatus aufrechterhalten, die Replikation verwalten und die Funktionsübernahme bearbeiten. Sollte ein Datenelement (Member) nicht mehr erreichbar sein, setzt Ihr Cluster seinen Betrieb trotzdem ordnungsgemäß fort.

## Plattenverschlüsselung

Für alle {{site.data.keyword.composeForPostgreSQL}}-Services erfolgt die Verschlüsselung im Ruhezustand. Ihre Daten befinden sich auf Servern, auf denen die Verschlüsselung auf Datenträgerebene aktiviert ist. 

Da es sich bei {{site.data.keyword.composeForPostgreSQL}} um einen verwalteten Service handelt, sind Operatoren von Compose auf {{site.data.keyword.cloud}} in der Lage, Daten zu sehen. Zusätzlich zur Plattenverschlüsselung wird empfohlen, persönliche Informationen zu verschlüsseln, bevor sie in der Datenbank gespeichert werden, oder Erweiterungen bzw. Features zu verwenden, um die Verschlüsselung auf der Datenbank selbst zu ermöglichen. Obwohl diese Methoden den Bedienungskomfort oder die Leistung beeinträchtigen können, hat es sich bewährt, den Schutz persönlicher Informationen mit Verschlüsselung sicherzustellen.

## Automatische Skalierung

Die Ressourcen werden basierend auf der Gesamtplattenspeicherbelegung der PostgreSQL-Datenbanken automatisch skaliert. Der Hauptspeicher basiert auf einem Faktor des bereitgestellten Plattenspeicherplatzes im Verhältnis von 1:4. Diese Ressourcen werden als Einheiten gebündelt.

Die automatische Skalierung ist so konzipiert, dass sie als Reaktion auf die kurz-bis mittelfristigen Trends Ihrer Datenbank erfolgt. Ihr Service wird in stündlichen Intervallen überprüft. Wenn der Plattenspeicherplatz für den Service knapp zu drohen wird, werden der Bereitstellung weitere Einheiten zugeordnet. 

Bei der automatischen Skalierung wird kein Scale-down für Bereitstellungen durchgeführt, bei denen sich die Platten-/Speicherbelegung verringert hat. Die für Ihre Datenbanken bereitgestellten Ressourcen bleiben für zukünftige Anforderungen weiterhin bestehen, sofern Sie Ihre Bereitstellung nicht per Scale-down manuell nach unten skalieren.
{: .tip}

## Rollen

Jeder PostgreSQL-Service wird mit der Rolle 'admin' bereitgestellt. Weitere Rollen und Berechtigungen können über psql hinzugefügt und verwaltet werden. Für diesen Service gibt es keine Rolle 'superuser'.

## Datenbankerweiterungen

Sie können PostgreSQL-Erweiterungen mit psql auflisten, installieren und verwalten.

Zum Ausführen der Befehle CREATE und ALTER müssen Sie die bereitgestellte Rolle 'admin' verwenden. {: .tip}

### Erweiterungen auflisten

Eine vollständige Liste der unterstützten Erweiterungen können Sie mit 'pg_available_extensions' abrufen.
`SELECT name FROM pg_available_extensions;`

### Erweiterungen installieren

Verwenden Sie zum Installieren einer beliebigen Erweiterung den Befehl 'CREATE extension'.
`CREATE extension <name> ;`

### Erweiterungen aktualisieren

Verwenden Sie zum Installieren einer neuen Version einer Erweiterung den Befehl 'ALTER EXTENSION'.
`ALTER EXTENSION <name> UPDATE TO <version>;`
