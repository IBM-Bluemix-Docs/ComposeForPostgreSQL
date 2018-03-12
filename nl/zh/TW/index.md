---

copyright:
  years: 2016,2018
lastupdated: "2017-10-16"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 關於 {{site.data.keyword.composeForPostgreSQL}}
{: #about-compose-for-postgresql}

{{site.data.keyword.composeForPostgreSQL_full}} 提供可高度自訂的強大開放程式碼物件導向資料庫。使用 Postgres，開發十分快速，而且可以輕鬆地擴充。您可以使用想要的語言（例如 C/C++、Perl、Python、TCL/TK、Delphi/Kylix、VB、PHP、ASP 及 Java）進行開發。您可以取得具有 JSON 支援之特性豐富的企業資料庫，提供最佳的 SQL 及 NoSQL 世界。
{:shortdesc}

**附註：**在 2016 年 9 月 14 日之前佈建且仍然作用中的任何 Compose 服務實例，仍然可以使用，而且可以在 [https://www.compose.com/](https://www.compose.com) 直接存取。在 {{site.data.keyword.cloud}} 帳戶內，可以直接存取及使用從此點往前佈建的任何 Compose 服務實例。

## 建立 {{site.data.keyword.composeForPostgreSQL}} 服務實例

您可以從 {{site.data.keyword.cloud_notm}} 型錄中的 [{{site.data.keyword.composeForPostgreSQL}} 頁面](https://console.{DomainName}/catalog/services/compose-for-postgresql/)建立 {{site.data.keyword.composeForPostgreSQL}} 服務。

選擇服務名稱、地區、組織，以及要在其中佈建服務的空間。您可以使用**選取資料庫版本**欄位，從可用的資料庫版本中進行選擇。

當您佈建 {{site.data.keyword.composeForPostgreSQL}} 實例時，可以選擇*標準* 或*企業* 方案。使用*企業* 方案，您可以將 {{site.data.keyword.composeForPostgreSQL}} 實例佈建到可用的 {{site.data.keyword.composeEnterprise}} 叢集。{{site.data.keyword.composeEnterprise}} 提供企業相符性所需的安全和隔離，並使用專用網路來確保已部署之資料庫的效能。如需詳細資料，請參閱 [Compose Enterprise 文件](../ComposeEnterprise/index.html)。

## 管理 {{site.data.keyword.composeForPostgreSQL}}

您可以從服務儀表板來管理服務。在這裡，您可以找到 {{site.data.keyword.cloud_notm}} Compose 資料庫的相關資訊，以及連接方式。您也可以：
- 管理備份
- 為您的服務配置更多資源
- 變更服務密碼
- 使用白名單來限制對資料庫的存取權。如需相關資訊，請參閱[設定](./dashboard-settings.html)。

## 連接至 {{site.data.keyword.composeForPostgreSQL}}
{: #connecting-to-compose-for-postgreSQL}

您可以使用與服務一起建立的認證，或使用服務儀表板的*概觀* 標籤中所提供的連線字串及指令行，來連接至服務。

## 將 {{site.data.keyword.cloud_notm}} 應用程式連接至 {{site.data.keyword.composeForPostgreSQL}}

若要將 {{site.data.keyword.cloud_notm}} 應用程式連接至服務，請使用與服務一起建立的認證。您可以在[連接 {{site.data.keyword.cloud_notm}} 應用程式](./connecting-bluemix-app.html)中，找到如何將 {{site.data.keyword.cloud_notm}} 應用程式連接至 {{site.data.keyword.composeForPostgreSQL}} 服務的資訊。

## 從 {{site.data.keyword.cloud_notm}}

 之外連接至 {{site.data.keyword.composeForPostgreSQL}}如果您想要從 {{site.data.keyword.cloud_notm}} 之外連接至 {{site.data.keyword.composeForPostgreSQL}}，則可以使用所提供的連線字串或指令行。您可以在[連接外部應用程式](./connecting-external.html)中，找到如何連接的相關資訊。
