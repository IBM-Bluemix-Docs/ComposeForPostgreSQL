---

copyright:
  years: 2016,2017
lastupdated: "2017-06-07"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Connecting a {{site.data.keyword.Bluemix_notm}} application

To connect a {{site.data.keyword.Bluemix_notm}} application to your service, use the service credentials that are created when the service is provisioned. The sample app demonstrates how to use Node.js to connect to a {{site.data.keyword.composeForPostgreSQL}} service using the provided credentials, and how to create a database and read from and write to the database.

## Connecting using the 'Hello World' sample app

The [compose-postgresql-helloworld-nodejs](https://github.com/IBM-Bluemix/compose-postgresql-helloworld-nodejs) sample app demonstrates how to use Node.js to connect to a {{site.data.keyword.composeForPostgreSQL}} service using the provided credentials. The application creates, reads from, and writes to a database

Download the sample app and follow the instructions in the readme file. Then, in your application details page in {{site.data.keyword.Bluemix_notm}}, click **View APP** to view the contents of the *examples* table.

## Available credentials

Field Name|Description
----------|-----------
`uri`|The URI to be used when connecting to the service. Includes the schema (`postgres:`), admin user name and password, host name of server, port number to connect to, database name and "?ssl=true" to enable SSL connections.
`uri_cli`|A `psql` shell command line that connects to the database instance.
`ca_certificate_base64`|A self-signed certificate that is used to confirm that an application is connecting to the appropriate server. This is base64 encoded. You need to decode the key before using it, as shown in the sample application.
`deployment_id`|An internal identifier for the service as created within Compose.
`db_type`|The type of database that is offered by the service; in this case `postgresql`.
`name`|The database deployment name.
{: caption="Table 1. Compose for PostgreSQL credentials" caption-side="top"}
