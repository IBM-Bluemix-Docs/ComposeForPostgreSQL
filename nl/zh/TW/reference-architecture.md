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

# 架構 
{: #architecture}

## 抄寫

{{site.data.keyword.composeForPostgreSQL_full}} 服務包含具有兩個資料成員的叢集：主導者及追隨者成員。資料會在兩個資料成員之間抄寫，且它們的磁碟空間會分散在地區的可用性區域。高可用性是使用 Patroni 來管理，其中三個 etcd 仲裁程序會維護叢集狀態、管理抄寫，以及處理失效接手。萬一某一個資料成員變成無法聯繫，您的叢集將繼續正常運作。

## 磁碟加密

所有 {{site.data.keyword.composeForPostgreSQL}} 服務都有靜態加密。您的資料位於已啟用磁區層次加密的伺服器上。 

由於 {{site.data.keyword.composeForPostgreSQL}} 是一項受管理的服務，因此 {{site.data.keyword.cloud}} Compose 操作員能夠看到資料。除了磁碟加密外，我們建議您也先將個人資訊加密，再將它儲存在資料庫中，或使用延伸或特性對資料庫本身啟用加密。這些方法固然可能影響可用性或效能，確定個人資訊受到加密保護仍是個很好的作法。

## 自動調整

資源會根據 PostgreSQL 資料庫的磁碟儲存空間總用量而自動調整。記憶體是以 1:4 的佈建磁碟空間比例為基礎。這些資源組合成為單位。

自動調整的設計是要回應資料庫的中短期趨勢。每小時都會檢查您的服務，如果它的磁碟空間不足，便會將更多的單位配置給該部署。 

自動調整對於磁碟/記憶體用量收縮的部署，不會將其縮減。針對您的資料庫佈建的資源將會保留以供您未來需要，或是直到您手動縮減部署為止。
{: .tip}

## 角色

每個 PostgreSQL 服務是以「管理」角色佈建。其他角色和許可權可以透過 psql 新增及管理。此服務沒有「超級使用者」角色。

## 資料庫延伸

使用 psql 來列出、安裝及管理 PostgreSQL 延伸。

您需要使用所提供的「管理者」角色來執行 CREATE 及 ALTER 指令。
{: .tip}

### 列出延伸

使用 pg_available_extensions 來取得完整的受支援延伸清單。
`SELECT name FROM pg_available_extensions;`

### 安裝延伸

使用 CREATE 延伸來安裝任何延伸。
`CREATE extension <name> ;`

### 更新延伸

使用 ALTER EXTENSION 來安裝新版本的延伸。
`ALTER EXTENSION <name> UPDATE TO <version>;`
