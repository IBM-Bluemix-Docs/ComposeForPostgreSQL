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

# Versões
{: #versions}

Versões Implementáveis | Versão Preferencial
----------|-----------
9.4.15, 9.5.10, 9.6.6 | 9.4.15, 9.5.10, 9.6.6
{: caption="Tabela 1. Versões do {{site.data.keyword.composeForPostgreSQL}}" caption-side="top"}

## Versão Preferencial

A versão preferencial é geralmente a mais recente do banco de dados PostgreSQL que está disponível para o {{site.data.keyword.composeForPostgreSQL}}. É a versão que é o padrão no seletor de versão suspensa na página do catálogo. Também é a versão que será provisionada automaticamente pela API se nenhuma versão for especificada na chamada.

### Novo Protocolo de Versão Preferencial

Quando uma nova versão for disponibilizada, sua liberação será anunciada e ela ficará disponível para implementação. Após a liberação, haverá uma janela de aproximadamente 7 dias na qual a versão mais recente estará disponível, mas não é a versão preferencial. Essa janela permite que você implemente e teste a nova versão, enquanto ainda tem a versão atual disponível. Ele também permite que os engenheiros do Compose localizem e corrijam quaisquer problemas que possam surgir na nova versão. No final da janela de 7 dias, a nova versão é configurada como a versão preferencial ou uma nova data para essa mudança é anunciada.

A lista de versões disponíveis para provisão está na [página de catálogo](https://console.{DomainName}/catalog/services/compose-for-postgresql) do {{site.data.keyword.composeForPostgreSQL}}.

Para obter uma lista atual de versões disponíveis para o serviço {{site.data.keyword.composeForPostgreSQL}}, é possível usar o terminal [GET /2016-07/deployments/:id/versions](https://apidocs.compose.com/v1.0/reference#2016-07-get-deployments-versions).
