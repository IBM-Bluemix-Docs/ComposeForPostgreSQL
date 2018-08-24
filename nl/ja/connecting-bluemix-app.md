---

copyright:
  years: 2016,2018
lastupdated: "2018-05-07"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# {{site.data.keyword.cloud_notm}} アプリケーションの接続

{{site.data.keyword.cloud}} アプリケーションをサービスに接続するには、サービスがプロビジョンされた時に作成されたサービス資格情報を使用します。 サンプル・アプリケーションは、用意されている資格情報を使用して Node.js で {{site.data.keyword.composeForPostgreSQL_full}} サービスに接続する方法と、データベースを作成し、データベースに対して読み書きを行う方法を示しています。

## 「Hello World」サンプル・アプリケーションを使用した接続

[compose-postgresql-helloworld-nodejs](https://github.com/IBM-Bluemix/compose-postgresql-helloworld-nodejs) サンプル・アプリケーションでは、用意されている資格情報に基づいて Node.js によって {{site.data.keyword.composeForPostgreSQL}} サービスに接続する方法を示しています。 このアプリケーションはデータベースを作成し、それに対して読み取りと書き込みを行います。

サンプル・アプリケーションをダウンロードし、README ファイル内の指示に従ってください。 その後、{{site.data.keyword.cloud_notm}} のアプリケーション詳細ページで**「アプリの表示」**をクリックして、*examples* 表の内容を表示してください。

## 使用可能な資格情報

フィールド名|説明
----------|-----------
`uri`|サービスに接続するときに使用する URI。 スキーマ (`postgres:`)、管理者ユーザー名とパスワード、サーバーのホスト名、接続先のポート番号、データベース名、SSL 接続を有効にする "?ssl=true" が含まれます。
`uri_cli`|データベース・インスタンスに接続する `psql` シェル・コマンド・ライン。
`ca_certificate_base64`|アプリケーションが適切なサーバーに接続されていることを確認するために使用する自己署名証明書。 これは base64 でエンコードされています。 サンプル・アプリケーションで示されているように、鍵をデコードした後に使用する必要があります。
`deployment_id`|Compose 内で作成された、サービスの内部 ID。
`db_type`|サービスによって提供されるデータベースのタイプ。この場合は、`postgresql`。
`name`|データベース・デプロイメント名。
`uri_direct_1`|サービスに接続するときに使用可能な 2 番目の URI。 形式は `uri` と同様です。
`uri_cli_1`|データベース・インスタンスに接続する 2 番目の `psql` シェル・コマンド・ライン。
{: caption="表 1. Compose for PostgreSQL の資格情報" caption-side="top"}

**注:** 2 つの `haproxy` ポータルは、PostgreSQL サービスへのアクセスを提供します。 接続するために `uri` と `uri_direct_1` の両方を使用できます。 アプリケーションで、接続障害の対応管理のために `uri` と `uri_direct_1` を切り替えます。
