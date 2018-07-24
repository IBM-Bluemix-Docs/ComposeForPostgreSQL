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

# Versions
{: #versions}

Deployable Versions | Preferred Version
----------|-----------
9.4.15, 9.5.10, 9.6.6 | 9.4.15, 9.5.10, 9.6.6
{: caption="Table 1. {{site.data.keyword.composeForPostgreSQL}} versions" caption-side="top"}

## Preferred Version

The preferred version is typically the newest version of the PostgreSQL database that is available for {{site.data.keyword.composeForPostgreSQL}}. It is the version that is the default in the drop-down version selector on the catalog page. It is also the version that is automatically provisioned by API if no version is specified in the call.

### New Preferred Version Protocol

When a new version is made available, its release will be announced and it will be available for deployment. Following release there is an approximately 7-day window where the newest version is available, but it is not the preferred version. This window allows you to deploy and test the new version, while still having the current version available. It also allows Compose engineers to spot and fix any issues that may arise in the new version. At the end of the 7-day window the new version is set as the preferred version, or a new date for this change is announced.

The list of versions available to provision is on the {{site.data.keyword.composeForPostgreSQL}} [catalog page](https://console.{DomainName}/catalog/services/compose-for-postgresql).

To get a current list of available versions for your {{site.data.keyword.composeForPostgreSQL}} service you can use the 
[GET /2016-07/deployments/:id/versions](https://apidocs.compose.com/v1.0/reference#2016-07-get-deployments-versions) endpoint.
