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

# Conectando um aplicativo externo
{: #connecting-external-app}

Há duas maneiras de conectar um aplicativo externo ao {{site.data.keyword.composeForPostgreSQL_full}}:

- Uma **Sequência de conexões** pode ser usada por algumas bibliotecas do cliente e contém todas as informações necessárias para outras bibliotecas se conectarem.

- **Linha de comandos** é um comando pré-formatado que chamará `psql` com os parâmetros corretos.

Você localizará ambos na página *Visão geral* de seu serviço {{site.data.keyword.composeForPostgreSQL}}.

## Conectando-se ao driver de uma linguagem

O Postgres tem uma vasta matriz de drivers de linguagem. A tabela cobre alguns dos mais comuns.

Idioma|Exemplos
----------|-----------
PHP|[pgsql](http://php.net/manual/en/pgsql.examples-basic.php)
Ruby|[ruby-pg](https://bitbucket.org/ged/ruby-pg/wiki/Home)
Ruby on Rails|[Guia do Ruby on Rails](http://edgeguides.rubyonrails.org/configuring.html#configuring-a-postgresql-database)
Python|[Psycopg2](https://wiki.postgresql.org/wiki/Psycopg2_Tutorial)
C#|[Open Database
Connectivity](https://wiki.postgresql.org/wiki/Using_Microsoft_.NET_with_the_PostgreSQL_Database_Server_via_ODBC)
Go|[pq](https://godoc.org/github.com/lib/pq)
Node|[node-postgres](https://github.com/brianc/node-postgres/wiki/Example)

## Conectando com a linha de comandos

**psql** é a ferramenta de linha de comandos para se conectar ao Postgres. Para usá-la, as ferramentas do cliente PostgreSQL precisarão ser instaladas no sistema local. Elas podem ser instaladas por meio da instalação do pacote PostgreSQL integral transferido por download do postgresql.org, de seus pacotes de sistemas operacionais ou no MacOS X com o brew instalado, execute `brew install postgresql`).   

É possível ler mais sobre psql na documentação do PostgreSQL - [referência](https://www.postgresql.org/docs/current/static/app-psql.html) e uma [introdução](http://postgresguide.com/utilities/psql.html) simples no Guia do Postgres.

É possível localizar o comando da linha de comandos que você precisa usar em seu painel de instância do {{site.data.keyword.composeForPostgreSQL}} na guia Visão geral.

```
psql "sslmode=require host=bluemix-sandbox-dal-9-portal.6.dblayer.com port=24761 dbname=compose user=admin"
```

Ao inserir o comando, você será solicitado para a senha, que é possível localizar nas informações de Sequência de conexões na mesma guia ou nas *Credenciais de serviço*.

## Conectando-se ao pgAdmin3

pgAdmin3 é um cliente de GUI popular para PostgreSQL. Use as etapas a seguir para conectar-se ao pgAdmin 3

1. Faça download e instale a versão do pgAdmin3 para seu sistema operacional por meio de [https://www.pgadmin.org/](https://www.pgadmin.org/).
2. Execute o pgAdmin3 e selecione "Incluir servidor" na barra de menus para criar uma nova conexão para abrir o painel *Novo registro de servidor*.

  ![New Server Registration panel in pgAdmin3. Properties tab.](./images/pgadmin.png "The properties tab of the New Server Registration panel in pgAdmin3.")

3. Conclua os campos no painel com as informações na página Visão geral de seu serviço {{site.data.keyword.composeForPostgreSQL}}:

  * **Nome**: pode ser qualquer coisa que descreva sua implementação do Postgres. Para simplificar, torne isso o mesmo nome que aquele usado no Compose.
  * **Host**: isso será por meio da parte do host de sua sequência de conexões.
  * **Porta**: isso será da parte da porta de sua sequência de conexões.
  * **Nome do usuário**: isso será o nome do usuário para um administrador ou um usuário que você criou.
  * **Senha**: isso será a senha para o administrador (localizado na seção Credenciais) ou um usuário que você criou.

4. Depois de concluir os campos, selecione a guia "SSL":

  ![New Server Registration panel in pgAdmin3. SSL tab.](./images/pgadmin_ssl.png "The SSL tab of the New Server Registration panel in pgAdmin3.")

5. Mude SSL para "require".
6. Clique em "OK" para salvar as configurações de conexão e se conectar ao banco de dados.
