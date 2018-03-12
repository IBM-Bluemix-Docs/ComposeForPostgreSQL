---

copyright:
  years: 2016,2018
lastupdated: "2018-01-03"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Preços
{: #pricing}

## Configuração base
Um serviço {{site.data.keyword.composeForPostgreSQL_full}} é um cluster com dois nós de dados, cada nó de dados contendo 1 GB de armazenamento e 102 MB de memória, que é igual a 1 unidade de recursos. O serviço _inclui_ replicação e alta disponibilidade, de maneira que cada unidade e o preço por unidade _inclua_ o custo dos recursos em ambos os nós.

A configuração base também inclui três cápsulas do árbitro etcd para gerenciar a replicação e duas cápsulas HAProxy para gerenciar conexões e failover. As cápsulas HAProxy têm 64 MB de memória cada uma.

### Total
A configuração de serviço de base tem um preço definido. Consulte o ladrilho de catálogo no {{site.data.keyword.cloud_notm}} para precificação base em sua moeda local. Por exemplo, o preço base em dólares americanos é US$ 12/mês.

## Opções de expansão
Se você precisar de armazenamento ou memória adicional para o seu serviço, será possível aumentar os recursos alocados em uma razão 10:1 de armazenamento em disco para unidade de memória. Aumentar o disco alocado para a implementação também aumentará a RAM alocada. Uma unidade do {{site.data.keyword.composeForPostgreSQL}} consiste em 1 GB de armazenamento e 102 MB de memória e cada unidade e o preço por unidade _incluem_ o custo para aumentar os recursos em ambos os nós de dados.

### Total
Cada unidade adicional (1 GB de armazenamento/102 MB de memória) tem um preço unitário, que é listado em sua moeda local no ladrilho de catálogo do {{site.data.keyword.cloud_notm}} para o serviço. Em dólares americanos cada unidade adicional custa US$ 12. Conforme o tamanho _total_ de todos os serviços do {{site.data.keyword.composeForPostgreSQL}} aumenta, o preço por unidade diminui, conforme mostrado na tabela de precificação em camadas, abaixo.

### Precificação em camadas
Número de unidades|Preço por unidade
----------|-----------
1 - 9 unidades|preço base por unidade -- US$ 12,00/Unidade
10 - 24 unidades|10% redução -- US$ 10,80/Unidade
25 - 49 unidades|20% redução -- US$ 9,60/Unidade
50 - 99 unidades|30% redução -- US$ 8,40/Unidade
100 - 499 unidades|40% redução -- US$ 7,20/Unidade
500 - 999 unidades|50% redução -- US$ 6,00/Unidade
1.000 - 4.999 unidades|60% redução -- US$ 4,80/Unidade
+ de 5.000 unidades|70% redução -- US$ 3,60/Unidade
{: caption="Tabela 1. Precificação em camadas do {{site.data.keyword.composeForPostgreSQL}}" caption-side="top"}
