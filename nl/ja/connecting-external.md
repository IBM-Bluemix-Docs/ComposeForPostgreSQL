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

# 外部アプリケーションの接続
{: #connecting-external-app}

{{site.data.keyword.composeForPostgreSQL_full}} に外部アプリケーションを接続するには、2 つの方法があります。

- 一部のクライアント・ライブラリーでは**接続ストリング**を使用できます。接続ストリングに、他のライブラリーからの接続に必要な情報をすべて組み込みます。

- **コマンド・ライン**は、形式の決まっているコマンドです。正しいパラメーターを指定して `psql` を呼び出します。

両方の方法が {{site.data.keyword.composeForPostgreSQL}} サービスの*「概要」*ページにあります。

## 言語のドライバーによる接続

Postgres には、さまざまな言語ドライバーがあります。一般的なドライバーを以下の表にまとめます。

言語|例
----------|-----------
PHP|[pgsql](http://php.net/manual/en/pgsql.examples-basic.php)
Ruby|[ruby-pg](https://bitbucket.org/ged/ruby-pg/wiki/Home)
Ruby on Rails|[Rails ガイド](http://edgeguides.rubyonrails.org/configuring.html#configuring-a-postgresql-database)
Python|[Psycopg2](https://wiki.postgresql.org/wiki/Psycopg2_Tutorial)
C#|[ODBC](https://wiki.postgresql.org/wiki/Using_Microsoft_.NET_with_the_PostgreSQL_Database_Server_via_ODBC)
Go|[pq](https://godoc.org/github.com/lib/pq)
Node|[node-postgres](https://github.com/brianc/node-postgres/wiki/Example)

## コマンド・ラインによる接続

Postgres に接続するためのコマンド・ライン・ツールは **psql** です。この機能を使用するには、ローカル・システムに PostgreSQL クライアント・ツールをインストールしておく必要があります。そのツールをインストールするには、postgresql.org でダウンロードした PostgreSQL パッケージ全体をオペレーティング・システム・パッケージからインストールします。brew をインストールした MacOS X の場合は、`brew install postgresql` を実行します。   

psql の詳細については、PostgreSQL の資料 ([リファレンス](https://www.postgresql.org/docs/current/static/app-psql.html)) と Postgres ガイドにあるシンプルな[概要](http://postgresguide.com/utilities/psql.html)を参照してください。

{{site.data.keyword.composeForPostgreSQL}} インスタンスのダッシュボードで使用するコマンド・ライン・コマンドは、「概要」タブで確認できます。

```
psql "sslmode=require host=bluemix-sandbox-dal-9-portal.6.dblayer.com port=24761 dbname=compose user=admin"
```

コマンドを入力すると、パスワードを求めるプロンプトが表示されます。パスワードは、同じタブにある接続ストリングの情報か*サービスの資格情報*で確認できます。

## pgAdmin3 による接続

pgAdmin3 は、PostgreSQL に対応した一般的な GUI クライアントです。pgAdmin3 で接続する場合は、以下の手順を実行します。

1. ご使用のオペレーティング・システムに対応したバージョンの pgAdmin3 を [https://www.pgadmin.org/](https://www.pgadmin.org/) からダウンロードしてインストールします。
2. pgAdmin3 を実行し、メニュー・バーから「Add Server」を選択し、新しい接続を作成して、*「New Server Registration」*パネルを開きます。

  ![pgAdmin3 の「New Server Registration」パネルの「Properties」タブ](./images/pgadmin.png "pgAdmin3 の「New Server Registration」パネルの「Properties」タブ")

3. {{site.data.keyword.composeForPostgreSQL}} サービスの「概要」ページの情報に基づいて、そのパネルの各フィールドに値を入力します。

  * **Name**: ご使用の Postgres デプロイメントに適した名前を設定します。わかりやすくするために、Compose で使用している名前をそのまま設定してください。
  * **Host**: 接続ストリングのホストの部分の値を設定します。
  * **Port**: 接続ストリングのポートの部分の値を設定します。
  * **Username**: ユーザー名として、admin か自分で作成したユーザー名を設定します。
  * **Password**: admin のパスワード (資格情報のセクションにある値) か自分で作成したユーザー名のパスワードを設定します。

4. 各フィールドに値を設定したら、「SSL」タブを選択します。

  ![pgAdmin3 の「New Server Registration」パネルの「SSL」タブ](./images/pgadmin_ssl.png "pgAdmin3 の「New Server Registration」パネルの「SSL」タブ")

5. SSL を「require」に変更します。
6. 「OK」をクリックして接続設定を保存し、データベースに接続します。
