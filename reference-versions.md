---
copyright:
  years: 2016,2018
lastupdated: "2018-06-12"

keywords: postgresql, compose

subcollection: compose-for-postgresql

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
9.4.20, 9.4.21 | 9.4.21
9.5.15, 9.5.16 | 9.5.16
9.6.11, 9.6.12 | 9.6.12
{: caption="Table 1. {{site.data.keyword.composeForPostgreSQL}} versions" caption-side="top"}

## Preferred Version

The preferred version is typically the newest version of the PostgreSQL database that is available for {{site.data.keyword.composeForPostgreSQL}}. It is the default version in the drop-down selector on the catalog page. It is also the version that is automatically provisioned by API if no version is specified in the call.

### New Preferred Version Protocol

When a new version is made available, its release is announced and it is available for deployment. Following release there is an approximately 7-day window where the newest version is available, but it is not the preferred version. This window allows you to deploy and test the new version, while still having the current version available. At the end of the 7-day window the new version is set as the preferred version, or a new date for this change is announced.

The list of versions available to provision is on the {{site.data.keyword.composeForPostgreSQL}} [catalog page](https://{DomainName}/catalog/compose-for-postgresql).

To get a current list of available versions for your {{site.data.keyword.composeForPostgreSQL}} service, you can use the [GET /2016-07/deployments/:id/versions] (https://apidocs.compose.com/v1.0/reference#2016-07-get-deployments-versions) endpoint.
