---

copyright:
  years: 2017
lastupdated: "2017-09-07"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 備份
{: #backups}

您可以從服務儀表板的*管理* 頁面中建立及下載備份。提供有排程備份及手動備份。

## 檢視現有備份

資料庫的每日備份是自動排定的。若要檢視現有備份，請導覽至服務儀表板的*管理* 頁面。 

![備份](./images/postgres-backups-show.png "服務儀表板中的備份清單")

按一下對應列來展開任何可用備份的選項。

![備份選項](./images/postgres-backups-options.png "備份的選項。") 

## 依需求建立備份

除了排程備份外，您也可以手動建立備份。若要建立手動備份，請導覽至服務儀表板的*管理* 頁面，然後按一下*立即備份*。

## 下載備份

若要下載備份，請導覽至服務儀表板的*管理* 頁面，然後針對您要下載的備份，按一下對應列中的*下載*。

## 備份內容

{{site.data.keyword.composeForPostgreSQL}} 備份會在您的執行中服務實例上使用 `pg_basebackup`。備份會製作叢集檔的二進位檔副本，並包括資料目錄中的所有檔案以及所有表格空間。備份還包括 WAL（預寫日誌）檔案，可用來將資料庫還原至 WAL 資料所涵蓋的時間點。

## 使用備份與本端資料庫搭配

您可以使用 {{site.data.keyword.composeForPostgreSQL}} 備份來執行資料庫的本端副本。備份的檔案結構容許將多個備份儲存在相同的目錄中；前幾個層次為 `data --> backup --> *datestamp*`。在有日期戳記的目錄內，您將找到 Snapshot 及 WAL 保存檔。

若要還原至本端資料庫，請執行下列動作：

1. 下載備份
2. 備份包含 README 檔：`data/backup/*timestamp*/snapshot/README`。在文字編輯器中開啟 README 檔。
3. 在本端下載並安裝 PostgreSQL。README 檔指出備份應該搭配執行的 PostgreSQL 版本。
4. 遵循 README 檔中的指示，以執行資料庫的本端副本。使用 `postgres -D conf` 指令，在 Snapshot 目錄內啟動您的本端 PostgreSQL。然後，您可以執行下列指令來連接至資料庫：`psql postgres -U focker`。

## 還原備份

若要將備份還原至新的服務實例，請遵循步驟來檢視現有備份，然後按一下對應列以展開您要下載之備份的選項。按一下**還原**按鈕。即會顯示一則訊息，讓您知道已起始還原。新的服務實例會自動命名為 "postgres-restore-[timestamp]"，而且在佈建開始時，儀表板上會出現這個實例。
