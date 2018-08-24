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

# Conectando um aplicativo {{site.data.keyword.cloud_notm}}

Para conectar um aplicativo {{site.data.keyword.cloud}} a seu serviço, use as credenciais de serviço que são criadas quando o serviço é provisionado. O app de amostra demonstra como usar Node.js para se conectar a um serviço {{site.data.keyword.composeForPostgreSQL_full}} usando as credenciais fornecidas e como criar um banco de dados e ler e gravar no banco de dados.

## Conectando usando o aplicativo de amostra 'Hello World'

O aplicativo de amostra [compose-postgresql-helloworld-nodejs](https://github.com/IBM-Bluemix/compose-postgresql-helloworld-nodejs) demonstra como usar o Node.js para se conectar a um serviço {{site.data.keyword.composeForPostgreSQL}} usando as credenciais fornecidas. O aplicativo cria, lê e grava em um banco de dados

Faça download do aplicativo de amostra e siga as instruções no arquivo leia-me. Em seguida, em sua página de detalhes do aplicativo no {{site.data.keyword.cloud_notm}}, clique em **Visualizar app** para visualizar os conteúdos da tabela *exemplos*.

## Credenciais disponíveis

Campo de nome|Descrição
----------|-----------
`uri`|O URI a ser usado na conexão com o serviço. Inclui o esquema (`postgres:`), o nome do usuário administrativo e a senha, o nome do host do servidor, o número da porta à qual se conectar, o nome do banco de dados e "?ssl=true" para ativar conexões SSL.
`uri_cli`|Uma linha de comando shell `psql` que se conecta à instância de banco de dados.
`ca_certificate_base64`|Um certificado autoassinado que é usado para confirmar se um aplicativo está se conectando ao servidor apropriado. Isso é codificado em base64. É preciso decodificar a chave antes de usá-la, conforme mostrado no aplicativo de amostra.
`deployment_id`|Um identificador interno para o serviço conforme criado no Compose.
`db_type`|O tipo de banco de dados que é oferecido pelo serviço; nesse caso, `postgresql`.
`name`|O nome da implementação do banco de dados.
`uri_direct_1`|Um URI secundário que pode ser usado ao se conectar ao serviço. Formatado como para `uri`.
`uri_cli_1`|Uma linha de comandos shell `psql` secundária que se conecta à instância de banco de dados.
{: caption="Tabela 1. Credenciais do Compose for PostgreSQL" caption-side="top"}

**Nota:** dois portais `haproxy` fornecem acesso ao serviço PostgreSQL. Tanto `uri` quanto `uri_direct_1` podem ser usados para a conexão. Em seus aplicativos, alterne entre `uri` e `uri_direct_1` para gerenciar respostas às falhas de conexão.
