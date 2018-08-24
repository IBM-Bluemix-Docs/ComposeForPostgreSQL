---

copyright:
  years: 2016,2018
lastupdated: "2018-03-27"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Informationen zu {{site.data.keyword.composeForPostgreSQL}}
{: #about-compose-for-postgresql}

{{site.data.keyword.composeForPostgreSQL_full}} bietet eine leistungsfähige objektbezogene Open-Source-Datenbank mit hoher Anpassbarkeit. Postgres ermöglicht die schnelle und leicht skalierbare Entwicklung. Die Entwicklung kann in einer Sprache erfolgen, mit der Sie vertraut sind, z. B. C/C++, Perl, Python, TCL/TK, Delphi/Kylix, VB, PHP, ASP oder Java. Sie erhalten eine mit vielen Funktionen ausgestattete Unternehmensdatenbank mit JSON-Unterstützung, mit der Sie das beste aus den zwei Welten SQL und NoSQL bekommen.
{:shortdesc}

**Hinweis:** Alle Compose-Serviceinstanzen, die vor dem 14. September 2016 bereitgestellt wurden und noch aktiv sind, können weiterhin verwendet werden und sind über [https://www.compose.com/](https://www.compose.com) zugänglich. Jede Compose-Serviceinstanz, die ab diesem Punkt bereitgestellt wird, ist direkt über Ihr {{site.data.keyword.cloud}}-Konto zugänglich und kann dort verwendet werden.

## {{site.data.keyword.composeForPostgreSQL}}-Serviceinstanz erstellen

Sie können einen {{site.data.keyword.composeForPostgreSQL}}-Service über die [{{site.data.keyword.composeForPostgreSQL}}-Seite](https://console.{DomainName}/catalog/services/compose-for-postgresql/) im {{site.data.keyword.cloud_notm}}-Katalog erstellen.

Wählen Sie einen Servicenamen und eine Region, eine Organisation und einen Bereich zur Bereitstellung des Service aus. Im Feld **Datenbankversion auswählen** können Sie eine der verfügbaren Datenbankversionen auswählen.

Bei der Bereitstellung Ihrer {{site.data.keyword.composeForPostgreSQL}}-Instanz können Sie den Plan *Standard* oder *Enterprise* auswählen. Mit dem Plan *Enterprise* können Sie Ihre {{site.data.keyword.composeForPostgreSQL}}-Instanz in einem {{site.data.keyword.composeEnterprise}}-Cluster bereitstellen. {{site.data.keyword.composeEnterprise}} stellt die für die Konformität mit Enterprise erforderliche Sicherheit und Isolation bereit und stellt mithilfe eines dedizierten Netzbetriebs die Leistung der bereitgestellten Datenbanken sicher. Weitere Details finden Sie in der Dokumentation zu [{{site.data.keyword.composeEnterprise}}](/docs/services/ComposeEnterprise/index.html).

## {{site.data.keyword.composeForPostgreSQL}} verwalten

Sie können Ihren Service über das Service-Dashboard verwalten. Hier finden Sie Informationen zu Ihrer {{site.data.keyword.cloud_notm}} Compose-Datenbank und dazu, wie Sie eine Verbindung zu ihr herstellen. Außerdem können Sie:
- Ihre Sicherungen verwalten
- Ihrem Service mehr Ressourcen zuordnen
- Das Servicekennwort ändern
- Whitelists verwenden, um den Zugriff auf Ihre Datenbank zu beschränken. 

Weitere Informationen finden Sie im Abschnitt [Einstellungen](./dashboard-settings.html).

{{site.data.keyword.composeForPostgreSQL}} nutzt Cloud Foundry-Rollen, um den Zugriff auf den Service zu verwalten. Nur Benutzer mit der Entwicklerrolle können das Service-Dashboard anzeigen oder verwenden. Weitere Informationen zu Cloud Foundry-Rollen finden Sie auf den Seiten [Cloud Foundry-Zugriff](https://console.bluemix.net/docs/iam/cfaccess.html#cfaccess) und [Cloud Foundry-Zugriff](https://console.bluemix.net/docs/iam/mngcf.html#mngcf) verwalten.
{: .tip}

## Verbindung zu {{site.data.keyword.composeForPostgreSQL}} herstellen
{: #connecting-to-compose-for-postgreSQL}

Sie können mit den Berechtigungsnachweisen, die zusammen mit Ihrem Service erstellt werden, oder mithilfe der Verbindungszeichenfolgen und der Befehlszeile, die auf der Registerkarte *Übersicht* Ihres Service-Dashboards bereitgestellt werden, eine Verbindung zu dem Service herstellen.

## Verbindung von einer {{site.data.keyword.cloud_notm}}-Anwendung zu {{site.data.keyword.composeForPostgreSQL}} herstellen

Um eine {{site.data.keyword.cloud_notm}}-Anwendung mit Ihrem Service zu verbinden, verwenden Sie die Berechtigungsnachweise, die zusammen mit dem Service erstellt wurden. Informationen zum Herstellen einer Verbindung von einer {{site.data.keyword.cloud_notm}}-Anwendung zu einem {{site.data.keyword.composeForPostgreSQL}}-Service finden Sie im Abschnitt [{{site.data.keyword.cloud_notm}}-Anwendung verbinden](./connecting-bluemix-app.html).

## Verbindung zu {{site.data.keyword.composeForPostgreSQL}} außerhalb von {{site.data.keyword.cloud_notm}} herstellen

Wenn Sie außerhalb von {{site.data.keyword.cloud_notm}} eine Verbindung zu {{site.data.keyword.composeForPostgreSQL}} herstellen wollen, können Sie dazu die bereitgestellten Verbindungszeichenfolgen oder die Befehlszeile verwenden. Informationen dazu, wie sich eine Verbindung herstellen lässt, finden Sie im Abschnitt [Externe Anwendung verbinden](./connecting-external.html).
