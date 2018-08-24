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

# Configuração da Conexão
{: #connection-configuration}

As conexões com o banco de dados do {{site.data.keyword.composeForPostgreSQL_full}} são gerenciadas por 2 portais HAProxy. Cada portal tem 64 MB de memória. Ter dois portais permitirá que os aplicativos mantenham a conectividade se um deles se tornar inacessível.

Failover no lado do cliente é responsabilidade do designer de aplicativo. Alguns drivers PostgreSQL manipulam múltiplas sequências de conexões e failovers normais automaticamente. A menos que esteja trabalhando com um driver que manipule completamente erros de failover, será necessário:

* Trabalhar com um driver que aceite múltiplos terminais em sua configuração de conexão.
* Assegurar que as suas chamadas de aplicativos leiam ou gravem adequadamente na reação do banco de dados a erros. As opções incluem:
  + Criar log do erro e reconectar.
  + Reconectar e tentar novamente a operação que causou o erro.
  + Enfileirar a operação com falha e planejar a reconexão.

## Criptografia em Trânsito

Todos os portais HAProxy do {{site.data.keyword.composeForPostgreSQL}} têm o TLS/SSL ativado e suportam o TLS versão 1.2. Os certificados para o serviço são certificados autoassinados. Talvez seja necessário salvar uma cópia local do certificado para seu serviço e fornecer seu local para que o driver de seu aplicativo faça uma conexão segura.

## Limites de Conexão

As conexões com o banco de dados têm um limite de conexão inicial de 100 conexões para o serviço. Dependendo dos recursos alocados para o serviço por meio de ajuste de escala automático ou manual, o limite de conexão terá o máximo de 1.000 conexões. Exceder o limite de conexão tornará seu serviço não responsivo.

É possível gerenciar conexões de seu aplicativo por meio do recurso de definição do conjunto de conexões do driver.
{: .tip}

## Tempos limite de proxy

Os portais HAProxy gerenciam o ciclo de vida de conexões entre o servidor e o cliente. Nós as detalhamos aqui como uma referência para gravadores de driver e outros que têm interesse na atividade de baixo nível de conexões com o banco de dados do {{site.data.keyword.composeForPostgreSQL}}.

Configurando | Value | Aplica
----------|-----------|-----------
cliente | 1 dia | Quando se espera que o cliente reconheça ou envie dados.
conectar | 4s | Quando uma conexão está sendo feita entre o proxy e o servidor.
server | 30m | Quando se espera que o servidor reconheça ou envie dados.
túnel | 1d | Quando uma conexão bidirecional é estabelecida entre um cliente e um servidor e a conexão permanece inativa em ambas as direções.
cliente-fin | 5m | Quando se espera que o cliente reconheça ou envie dados enquanto uma direção já está encerrada.
check | 5s | Como uma verificação de tempo limite secundário quando uma conexão está sendo feita entre o proxy e o servidor.

{: caption="Tabela 1. Tempos limites de HAProxy do PostgreSQL" caption-side="top"}
