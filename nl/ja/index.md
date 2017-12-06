---

copyright:
  years: 2016,2017
lastupdated: "2017-10-16"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Compose for PostgreSQL の概説
{: #getting-started-with-compose-for-postgreSQL}

{{site.data.keyword.composeForPostgreSQL_full}} は、高度にカスタマイズ可能な、強力なオープン・ソースのオブジェクト関係データベースです。Postgres を使用すると、迅速で拡張が容易な開発が可能になります。C/C++、Perl、Python、TCL/TK、Delphi/Kylix、VB、PHP、ASP、Java など、使い慣れた言語で開発できます。JSON をサポートする機能が豊富なエンタープライズ・データベースを使用できるので、SQL と NoSQL の両領域のメリットが得られます。
{:shortdesc}

**注:** 2016 年 9 月 14 日より前にプロビジョンされた、現在もアクティブな Compose サービス・インスタンスは引き続き使用可能で、[https://www.compose.com/](https://www.compose.com) から直接アクセスできます。その時点以降にプロビジョンされた Compose サービス・インスタンスは、{{site.data.keyword.cloud}} アカウント内で直接アクセスして使用されます。

## Compose for PostgreSQL サービス・インスタンスの作成

[{{site.data.keyword.composeForPostgreSQL}} インスタンスを作成します](https://console.ng.bluemix.net/catalog/services/compose-for-postgresql/)。

サービスのインスタンスを作成するときは、必ずサービスの名前と資格情報名の両方を選択してください。サービスをバインドしないでおきます。サービスをプロビジョンするときに指定される資格情報を使用して、アプリケーションをサービスに接続できます。*使用可能な資格情報*セクションには、各種の資格情報値がリストされています。

{{site.data.keyword.composeForPostgreSQL}} インスタンスのプロビジョンでは、*標準*プランと*エンタープライズ*・プランのどちらかを選択できます。*エンタープライズ*・プランの場合は、{{site.data.keyword.composeForPostgreSQL}} インスタンスを使用可能な {{site.data.keyword.composeEnterprise}} クラスターにプロビジョンできます。{{site.data.keyword.composeEnterprise}} は、企業コンプライアンスで要求されるセキュリティーと分離を提供し、専用ネットワーキングを使用してデプロイ済みデータベースのパフォーマンスを確保します。詳しくは、[Compose Enterprise 文書](../ComposeEnterprise/index.html)を参照してください。

## Compose for PostgreSQL の管理

サービス・ダッシュボードからサービスを管理できます。ダッシュボードには {{site.data.keyword.cloud_notm}} Compose データベースとそれへの接続方法に関する情報が示されます。また、以下の操作を行うこともできます。
- バックアップを管理する
- サービスに割り振るリソースを増やす
- サービス・パスワードを変更する
- ホワイトリストを使用してデータベースへのアクセスを制限する
詳しくは、[設定](./dashboard-settings.html)を参照してください。

## Compose for PostgreSQL への接続
{: #connecting-to-compose-for-postgreSQL}

サービスに接続するには、サービスと一緒に作成された資格情報を使用するか、サービス・ダッシュボードの*「概要」*タブに表示される接続ストリングとコマンド・ラインを使用します。

## {{site.data.keyword.cloud_notm}} アプリケーションを Compose for PostgreSQL に接続する場合

{{site.data.keyword.cloud_notm}} アプリケーションをサービスに接続するには、サービスと一緒に作成された資格情報を使用します。{{site.data.keyword.cloud_notm}} アプリケーションを {{site.data.keyword.composeForPostgreSQL}} サービスに接続する方法については、[{{site.data.keyword.cloud_notm}} アプリケーションの接続](./connecting-bluemix-app.html)を参照してください。

## {{site.data.keyword.cloud_notm}} の外部から Compose for PostgreSQL に接続する場合

{{site.data.keyword.cloud_notm}} の外部から {{site.data.keyword.composeForPostgreSQL}} に接続する場合は、用意されている接続ストリングやコマンド・ラインを使用できます。接続方法については、[外部アプリケーションの接続](./connecting-external.html)を参照してください。
