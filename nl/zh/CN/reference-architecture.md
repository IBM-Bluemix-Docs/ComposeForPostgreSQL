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

# 体系结构 
{: #architecture}

## 复制

{{site.data.keyword.composeForPostgreSQL_full}} 服务包含一个具有两个数据成员的集群；一个领导成员，一个下属成员。数据会在两个数据成员之间进行复制，成员磁盘空间分布在区域的可用性专区中。高可用性通过 Patroni 进行管理，其中三个 etcd 判优程序分别负责维护集群状态、管理复制和处理故障转移。如果一个数据成员变为不可访问，集群仍会继续正常运行。

## 磁盘加密

所有 {{site.data.keyword.composeForPostgreSQL}} 服务都具有静态加密。数据位于启用了卷级别加密的服务器上。 

由于 {{site.data.keyword.composeForPostgreSQL}} 是受管服务，因此 {{site.data.keyword.cloud}} Compose 操作员可以查看数据。除了磁盘加密外，还建议您在数据库中存储个人信息之前，对这些信息加密，或者使用扩展或功能启用对数据库本身的加密。虽然这些方法可能会影响可用性或性能，但确保个人信息受到加密保护是比较好的做法。

## 自动扩展

资源将根据 PostgreSQL 数据库的磁盘存储总使用量自动进行扩展。内存基于按 1:4 比率供应的磁盘空间。这些资源会捆绑为单元。

自动扩展旨在响应数据库的中短期趋势。系统每小时会检查一次服务，如果服务的磁盘空间不足，那么会向部署分配更多单元。 

自动扩展不会向下扩展部署，即减少磁盘/内存使用量。向数据库供应的资源将保留以满足您的未来需求，或者直到您手动向下扩展部署为止。
{: .tip}

## 角色

每个 PostgreSQL 服务都供应有“管理员”角色。其他角色和许可权可以通过 psql 进行添加和管理。此服务没有“超级用户”角色。

## 数据库扩展

使用 psql 来列出、安装和管理 PostgreSQL 扩展。

您需要使用提供的“管理员”角色来运行 CREATE 和 ALTER 命令。
{: .tip}

### 列出扩展

使用 pg_available_extensions 来获取受支持扩展的完整列表。
`SELECT name FROM pg_available_extensions;`

### 安装扩展

使用 CREATE 扩展来安装任何扩展。
`CREATE extension <name> ;`

### 更新扩展

使用 ALTER EXTENSION 来安装扩展的新版本。
`ALTER EXTENSION <name> UPDATE TO <version>;`
