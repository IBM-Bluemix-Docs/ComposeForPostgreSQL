---

copyright:
  years: 2017
lastupdated: "2017-06-07"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Connecting to Compose for PostgreSQL using connection strings
{: #connecting-to-compose-for-postgreSQL-with-connection-strings}

Depending on the driver used by a language, there are a number of different schemes used to express how to connect to PostgreSQL. {{site.data.keyword.composeForPostgreSQL}} uses a URI format, the Connection string. The connection string is formatted as so:

```
postgres://[username]:[password]@[host]:[port]/[database]
```

You can find this connection string on your {{site.date.keyword.composeForPostgreSQL}} service Overview page.

## Connecting with a language's driver

Postgres has a vast array of language drivers. The table covers a few of the most common.
