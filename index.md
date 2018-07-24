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

# About {{site.data.keyword.composeForPostgreSQL}}
{: #about-compose-for-postgresql}

{{site.data.keyword.composeForPostgreSQL_full}} provides a powerful, open source object-relational database that is highly customizable. With Postgres, development is fast and easily scalable. You can develop in a language that you're comfortable with, such as C/C++, Perl, Python, TCL/TK, Delphi/Kylix, VB, PHP, ASP, and Java. You get a feature-rich enterprise database with JSON support, giving you the best of both the SQL and NoSQL worlds.
{:shortdesc}

**Note:** Any Compose service instances that were provisioned before 14 September 2016 that are still active can still be used and directly accessed at [https://www.compose.com/](https://www.compose.com). Any Compose service instance that is provisioned from this point forward is directly accessed and used within your {{site.data.keyword.cloud}} account.

## Creating a {{site.data.keyword.composeForPostgreSQL}} service instance

You can create a {{site.data.keyword.composeForPostgreSQL}} service from the [{{site.data.keyword.composeForPostgreSQL}} page](https://console.{DomainName}/catalog/services/compose-for-postgresql/) in the {{site.data.keyword.cloud_notm}} catalog.

Choose a service name, and a region, organization and space to provision the service in. You can use the **Select a database version** field to choose from the available database versions.

When you provision your {{site.data.keyword.composeForPostgreSQL}} instance you can choose the *Standard* or *Enterprise* plans. With the *Enterprise* plan, you can provision your {{site.data.keyword.composeForPostgreSQL}} instance into an available {{site.data.keyword.composeEnterprise}} cluster. {{site.data.keyword.composeEnterprise}} provides the security and isolation required by enterprise compliance and uses dedicated networking to ensure the performance of the deployed databases. See the [{{site.data.keyword.composeEnterprise}} documentation](/docs/services/ComposeEnterprise/index.html) for more details.

## Managing {{site.data.keyword.composeForPostgreSQL}}

You can manage your service from the service dashboard. Here you can find information about your {{site.data.keyword.cloud_notm}} Compose database and how to connect to it. You can also:
- manage your backups
- allocate more resources for your service
- change the service password
- use whitelists to restrict access to your databases. 

For more information, see [Settings](./dashboard-settings.html).

{{site.data.keyword.composeForPostgreSQL}} relies on Cloud Foundry roles to manage access to the service. Only users with the Developer role can see or use the service dashboard. For more information on Cloud Foundry roles, see the [Cloud Foundry access](https://console.bluemix.net/docs/iam/cfaccess.html#cfaccess) and the [Managing Cloud Foundry access](https://console.bluemix.net/docs/iam/mngcf.html#mngcf) pages.
{: .tip}

## Connecting to {{site.data.keyword.composeForPostgreSQL}}
{: #connecting-to-compose-for-postgreSQL}

You can connect to your service using the credentials that are created along with the service, or with the connection strings and command line that are provided in the *Overview* tab of your service dashboard.

## Connecting an {{site.data.keyword.cloud_notm}} application to {{site.data.keyword.composeForPostgreSQL}}

To connect an {{site.data.keyword.cloud_notm}} application to your service, use the credentials that are created along with the service. You can find information on how to connect an {{site.data.keyword.cloud_notm}} application to a {{site.data.keyword.composeForPostgreSQL}} service in [Connecting an {{site.data.keyword.cloud_notm}} Application](./connecting-bluemix-app.html).

## Connecting to {{site.data.keyword.composeForPostgreSQL}} from outside {{site.data.keyword.cloud_notm}}

If you want to connect to {{site.data.keyword.composeForPostgreSQL}} from outside {{site.data.keyword.cloud_notm}}, you can use the provided connection strings or command line. You can find information on how to connect in [Connecting an external application](./connecting-external.html).
