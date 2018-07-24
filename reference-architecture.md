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

# Architecture 
{: #architecture}

## Replication

An {{site.data.keyword.composeForPostgreSQL_full}} service contains a cluster with two data members; a leader and a follower member. Data is replicated across both data members, and their disk space is spread over the region's availablity zones.  High-availability is managed with Patroni, where three etcd arbiters maintain cluster state, manage replication, and handle failover. Should one data member become unreachable, your cluster will continue to operate normally.

## Disk Encryption

All {{site.data.keyword.composeForPostgreSQL}} services all have encryption at rest. Your data resides on servers that have volume-level encryption enabled. 

Because this is {{site.data.keyword.composeForPostgreSQL}} is a managed service, it is possible for {{site.data.keyword.cloud}} Compose operators to see data. In addition to the disk encryption, we recommend you encrypt personal information before storing it in the database or use extensions or features to enable encryption on the database itself. While these methods might impact usability or performance, it is good practice to ensure that personal information is protected with encryption.

## Auto-scaling

Resources are scaled automatically based on the total disk storage use of the PostgreSQL databases. Memory is based on a ratio of provisioned disk space at 1:4. These resources are bundled as units.

Auto-scaling is designed to respond to the short-to-medium term trends of your database. Every hour, your service is checked and if it is running short on disk space, then more units are allocated to the deployment. 

Auto-scaling does not scale down deployments where disk/memory usage has shrunk. The resources provisioned to your databases will remain for your future needs, or until you scale down your deployment manually.
{: .tip}

## Roles

Every PostgreSQL service is provisioned with an "admin" role. Other roles and permissions can be added and managed through psql. There is no "superuser" role for this service.

## Database Extensions

Use psql to list, install, and manage PostgreSQL extensions.

You need to use the provided "admin" role to run the CREATE and ALTER commands. {: .tip}

### Listing extensions

Use pg_available_extensions to get a full list of supported extensions.
`SELECT name FROM pg_available_extensions;`

### Installing extensions

Use CREATE extension to install any extension.
`CREATE extension <name> ;`

### Updating extensions

Use ALTER EXTENSION to install a new version of an extension.
`ALTER EXTENSION <name> UPDATE TO <version>;`
