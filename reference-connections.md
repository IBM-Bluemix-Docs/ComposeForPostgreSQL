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

# Connection Configuration
{: #connection-configuration}

{{site.data.keyword.composeForPostgreSQL_full}} database connections are managed by 2 HAProxy portals. Each portal has 64 MB of memory. Having two portals allows for applications to maintain connectivity if one of the portals becomes unreachable.

Failover at the client side is the responsibility of the application designer. Some PostgreSQL drivers handle multiple connection strings and graceful failover automatically. Unless you are working with a driver that completely handles failover errors, take the following steps:

* Work with a driver that accepts multiple endpoints in its connection configuration.
* Ensure your applications calls to read or write to the database react to errors appropriately. Options include:
  + Logging the error and reconnecting.
  + Reconnecting and retrying the operation that caused the error.
  + Queuing the failed operation and scheduling reconnection.

## Encryption in Transit

All {{site.data.keyword.composeForPostgreSQL}} HAProxy portals have TLS/SSL enabled and support TLS version 1.2. The certificates for the service are self-signed certificates. You might have to save a local copy of the certificate for your service and provide its location to your application's driver to make a secure connection.

## Connection Limits

Database connections have an initial limit of 100 connections for the service. Depending on the resources you allocate to the service through automatic or manual scaling, the connection limit will max out at 1000 connections. Exceeding the connection limit will make your service unresponsive.

You can manage connections from your application through your driver's connection pooling feature.
{: tip}

## Proxy Timeouts

The HAProxy portals manage the lifecycle of connections between the server and client. They are included here as a reference for driver writers and others who have an interest in the low-level activity of {{site.data.keyword.composeForPostgreSQL}} database connections.

Setting | Value | Applies
----------|-----------|-----------
`client` | 1 day | When the client is expected to acknowledge or send data.
`connect` | 4 s | When a connection is being made between the proxy and the server.
`server` | 30 m | When the server is expected to acknowledge or send data.
`tunnel` | 1 d | When a bidirectional connection is established between a client and a server, and the connection remains inactive in both directions.
`client-fin` | 5 m | When the client is expected to acknowledge or send data while one direction is already shut down.
`check` | 5 s | As a secondary timeout check when a connection is being made between the proxy and the server.

{: caption="Table 1. PostgreSQL HAProxy timeouts" caption-side="top"}
