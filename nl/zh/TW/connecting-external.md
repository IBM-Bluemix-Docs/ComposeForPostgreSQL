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

# 連接外部應用程式
{: #connecting-external-app}

將外部應用程式連接至 {{site.data.keyword.composeForPostgreSQL_full}} 的方式有兩種：

- **連線字串**可由某些用戶端程式庫使用，且包含其他程式庫進行連接時所需的一切資訊。

- **指令行**是一個預先格式化的指令，它會使用正確的參數來呼叫 `psql`。

您將在 {{site.data.keyword.composeForPostgreSQL}} 服務的*概觀* 頁面上找到這兩者。

## 使用語言的驅動程式連接

Postgres 具有一系列的各種語言驅動程式。此表格涵蓋一些最常見的語言驅動程式。

語言|範例
----------|-----------
PHP|[pgsql](http://php.net/manual/en/pgsql.examples-basic.php)
Ruby|[ruby-pg](https://bitbucket.org/ged/ruby-pg/wiki/Home)
Ruby on Rails|[Rails guide](http://edgeguides.rubyonrails.org/configuring.html#configuring-a-postgresql-database)
Python|[Psycopg2](https://wiki.postgresql.org/wiki/Psycopg2_Tutorial)
C#|[ODBC](https://wiki.postgresql.org/wiki/Using_Microsoft_.NET_with_the_PostgreSQL_Database_Server_via_ODBC)
Go|[pq](https://godoc.org/github.com/lib/pq)
Node|[node-postgres](https://github.com/brianc/node-postgres/wiki/Example)

## 使用指令行連接

**psql** 是用來連接至 Postgres 的指令行工具。若要使用它，必須在本端系統上安裝 PostgreSQL 用戶端工具。其安裝方式為從您的作業系統套件或在已安裝 brew 的 MacOS X 上，安裝從 postgresql.org 下載的完整 PostgreSQL 套件（執行 `brew install postgresql`）。   

您可以在 PostgreSQL 文件的[參照](https://www.postgresql.org/docs/current/static/app-psql.html)中，以及在《Postgres 手冊》的[簡介](http://postgresguide.com/utilities/psql.html)中閱讀更多 psql 的相關資訊。

您可以從「概觀」標籤中，找到您需要在 {{site.data.keyword.composeForPostgreSQL}} 實例儀表板中使用的指令行指令。

```
psql "sslmode=require host=bluemix-sandbox-dal-9-portal.6.dblayer.com port=24761 dbname=compose user=admin"
```

當您輸入指令時，系統會提示您輸入密碼，您可以在相同標籤上的「連線字串」資訊中，或在*服務認證* 中找到該密碼。

## 使用 pgAdmin3 連接

pgAdmin3 是 PostgreSQL 的常用 GUI 用戶端。請使用下列步驟，利用 pgAdmin 3 進行連接

1. 從 [https://www.pgadmin.org/](https://www.pgadmin.org/) 下載並安裝作業系統適用的 pgAdmin3 版本。
2. 執行 pgAdmin3 ，然後從功能表列中選取「新增伺服器」來建立新的連線，以開啟*新建伺服器登錄* 畫面。

  ![pgAdmin3 中的「新建伺服器登錄」畫面。「內容」標籤。](./images/pgadmin.png "pgAdmin3 中「新建伺服器登錄」畫面的內容標籤。")

3. 請使用 {{site.data.keyword.composeForPostgreSQL}} 服務的「概觀」頁面中的資訊，完成畫面中的欄位：

  * **名稱**：可以是說明 Postgres 部署的任何名稱。為了簡單起見，請讓這個名稱與 Compose 中所使用的名稱相同。
  * **主機**：這將是來自連線字串的主機部分。
  * **埠**：這將是來自連線字串的埠部分。
  * **使用者名稱**：這將是管理者或您所建立之使用者的使用者名稱。
  * **密碼**：這將是管理者（位於「認證」區段中）或您所建立之使用者的密碼。

4. 完成欄位之後，請選取 "SSL" 標籤：

  ![pgAdmin3 中的「新建伺服器登錄」畫面。SSL 標籤。](./images/pgadmin_ssl.png "pgAdmin3 中「新建伺服器登錄」畫面的 SSL 標籤。")

5. 將 SSL 變更為 "require"。
6. 按一下「確定」以儲存連線設定，並連接至資料庫。
