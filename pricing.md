---

copyright:
  years: 2016,2018
lastupdated: "2018-01-03"

keywords: postgresql, compose

subcollection: ComposeForPostgreSQL

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Pricing
{: #pricing}

## Base Configuration

An {{site.data.keyword.composeForPostgreSQL_full}} service is a cluster with two data nodes. Each data node contains 1 GB storage and 102 MB of memory, which is equal to one unit of resources. The service _includes_ replication and high-availability, so each unit and the price per unit _includes_ the cost of the resources across both nodes.

The base configuration also includes three etcd arbiter capsules to manage replication, and two HAProxy capsules for managing connections and fail-over. The HAProxy capsules each have 64 MB of memory.

The base service configuration has a set price. Consult the catalog tiles on {{site.data.keyword.cloud_notm}} for base pricing in your local currency. For example, the base price in US dollars is $12/month.

## Increasing resources

If you need extra storage or memory for your service, you can increase the resources that are allocated in a 10:1 ratio of disk storage to memory unit. Increasing the disk allocated to the deployment also increases the RAM allocated. A {{site.data.keyword.composeForPostgreSQL}} unit consists of 1 GB of storage and 102 MB of memory, and each unit and the price per unit _includes_ the cost to increase the resources on both data nodes.

## Calculating the cost of your deployment
{: #tiered-pricing}

Each additional unit (1 GB storage/102 MB memory) has a per unit price, which is listed in your local currency on the {{site.data.keyword.cloud_notm}} catalog tile for the service. In US dollars each additional unit costs $12. As the _total_ size of all your {{site.data.keyword.composeForPostgreSQL}} services increases, the per unit price decreases, as shown in the tiered pricing table.

Number of Units|Price per Unit
----------|-----------
1 - 9 units|Base price per unit - $12.00 USD/Unit
10 - 24 units|10% reduction - $10.80 USD/Unit
25 - 49 units|20% reduction - $9.60 USD/Unit
50 - 99 units|30% reduction - $8.40 USD/Unit
100 - 499 units|40% reduction - $7.20 USD/Unit
500 - 999 units|50% reduction - $6.00 USD/Unit
1,000 - 4,999 units|60% reduction - $4.80 USD/Unit
5,000+ units|70% reduction - $3.60 USD/Unit
{: caption="Table 1. {{site.data.keyword.composeForPostgreSQL}} tiered pricing" caption-side="top"}
