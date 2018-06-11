---

copyright:
  years: 2017,2018
lastupdated: "2018-03-02"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 备份
{: #backups}

您可以从服务仪表板_管理_页面的_备份_选项卡创建和下载备份。有每日、每周、每月和按需备份可用。备份按照以下安排保留：

备份类型|保留安排
----------|-----------
每日|每日备份保留 7 天
每周|每周备份保留 4 周
每月|每月备份保留 3 个月
按需|保留一个按需备份。保留的备份始终是最新的按需备份。
{: caption="表 1. 备份保留安排" caption-side="top"}

备份安排和保留策略已经过修订。如果需要保留的备份数多于保留安排允许的量，那么应该根据业务需求下载备份并保留归档。

## 查看现有备份

数据库的每日备份会自动安排。要查看现有备份，请浏览至服务仪表板的*管理*页面。 

  ![备份](./images/postgres-backups-show.png "服务仪表板中备份的列表")

单击相应的行以展开任何可用备份的选项。

  ![备份选项](./images/postgres-backups-options.png "备份选项") 

### 使用 API 查看现有备份

`GET /2016-07/deployments/:id/backups` 端点提供备份列表。将在服务的_概述_中显示基础端点以及服务实例标识和部署标识。例如： 
``` 
https://composebroker-dashboard-public.mybluemix.net/api/2016-07/instances/$INSTANCE_ID/deployments/$DEPLOYMENT_ID/backups
```  

## 随需应变创建备份

除了已安排的备份，您还可以手动创建备份。要创建手动备份，请浏览至服务仪表板的*管理*页面，然后单击*立即备份*。

### 使用 API 创建备份

向备份端点发送 POST 请求以启动手动备份：`POST /2016-07/deployments/:id/backups`。其将在运行时立即返回诀窍标识以及有关备份的信息。您必须检查备份端点以查看备份是否已完成，并在使用前查找其 backup_id。使用 `GET /2016-07/deployments/:id/backups/`。

## 下载备份

要下载备份，请浏览至服务仪表板的*管理*页面，然后单击要下载的备份相应行中的*下载*。

### 使用 API 下载备份

在服务的_备份_页面上查找要从其复原的备份并复制 backup_id，或者使用 `GET /2016-07/deployments/:id/backups` 以通过 Compose API 查找备份及其 backup_id。然后，使用 backup_id 以查找特定备份的信息和下载链接：`GET /2016-07/deployments/:id/backups/:backup_id`。

## 备份内容

{{site.data.keyword.composeForPostgreSQL}} 备份对您正在运行的服务实例使用 `pg_basebackup`。该备份会生成集群文件的二进制副本，并包含数据目录和所有表空间中的所有文件。该备份还包含 WAL（预写式日志）文件，可用于将数据库复原到 WAL 数据涵盖的时间点。

## 将备份与本地数据库配合使用

您可以使用 {{site.data.keyword.composeForPostgreSQL}} 备份来运行数据库的本地副本。备份的文件结构允许将多个备份存储在同一个目录中；最上面几个级别是 `data --> backup --> *datestamp*`。在具有日期戳的目录中，您将找到快照和 WAL 归档。

要复原到本地数据库，请执行以下操作：

1. 下载备份
2. 备份包含自述文件：`data/backup/*timestamp*/snapshot/README`。在文本编辑器中打开自述文件。
3. 在本地下载并安装 PostgreSQL。自述文件指示应与备份一起运行的 PostgreSQL 的版本。
4. 遵循自述文件中的指示信息来运行数据库的本地副本。使用 `postgres -D conf` 命令在快照目录中启动本地 PostgreSQL。然后，可以通过运行以下命令连接到数据库：`psql postgres -U focker`。

## 复原备份

要将备份复原到新服务实例，请执行以下步骤以查看现有备份，然后单击相应的行以展开要下载的备份的选项。单击**复原**按钮。此时将显示一条消息，通知您已启动复原。新服务实例将自动命名为“postgres-restore-[timestamp]”，并在供应启动时显示在仪表板上。

### 通过 {{site.data.keyword.cloud_notm}} CLI 复原

通过 {{site.data.keyword.cloud_notm}} CLI，使用以下步骤将备份从正在运行的 PostgreSQL 服务复原到新的 PostgreSQL 服务。 
1. 如果需要，请[下载并安装](https://console.bluemix.net/docs/cli/index.html#overview)。 
2. 在服务的_备份_页面上查找要从其复原的备份，然后复制备份标识。  
  **或者**  
使用 `GET /2016-07/deployments/:id/backups` 以通过 Compose API 查找备份及其标识。将在服务的_概述_中显示基础端点和服务实例标识。例如： 
  ``` 
  https://composebroker-dashboard-public.mybluemix.net/api/2016-07/instances/$INSTANCE_ID/deployments/$DEPLOYMENT_ID/backups
  ```  
响应将包含该服务实例的所有可用备份的列表。选取要从其复原的备份并复制其标识。

3. 使用相应的帐户和凭证登录。`bx login`（或 `bx login -help` 以查看所有登录选项）。

4. 切换到您的组织和空间：`bx target -o "$YOUR_ORG" -s "YOUR_SPACE"`

5. 使用 `service create` 命令以供应新服务，并提供在 JSON 对象中复原的源服务和特定备份。例如：
``` 
bx service create SERVICE PLAN SERVICE_INSTANCE_NAME -c '{"source_service_instance_id": "$SERVICE_INSTANCE_ID", "backup_id": "$BACKUP_ID" }'
```
_SERVICE_ 字段应该为 compose-for-postgresql，而 _PLAN_ 字段应该为 Standard 或 Enterprise（取决于环境）。_SERVICE\_INSTANCE\_NAME_ 是放置新服务名称的位置。_source\_service\_instance\_id_ 是备份源的服务实例标识；可通过运行 `bx cf service DISPLAY_NAME --guid` 获取，其中 _DISPLAY\_NAME_ 是备份源自的 PostgreSQL 服务的名称。 
  
  企业用户还需要在 JSON 对象中使用 `"cluster_id": "$CLUSTER_ID"` 参数指定要部署到的集群。
  
### 迁移到新版本

某些主版本升级在当前正在运行的部署中不可用。您将需要供应正在运行升级版本的新服务，然后使用备份迁移数据。此过程与上面的复原备份相同，但将指定要升级到的版本。

``` 
bx service create SERVICE PLAN SERVICE_INSTANCE_NAME -c '{"source_service_instance_id": "$SERVICE_INSTANCE_ID", "backup_id": ""$BACKUP_ID", "db_version":"$VERSION_NUMBER" }'
```

例如，将较旧版本的 {{site.data.keyword.composeForPostgreSQL}} 服务复原到运行 PostgreSQL 9.6.6 的新服务类似于以下示例：
```
bx service create compose-for-postgresql Standard migrated_postgres -c '{ "source_service_instance_id": "0269e284-dcac-4618-89a7-f79e3f1cea6a", "backup_id":"5a96d8a7e16c090018884566", "db_version":"9.6.6"  }'
