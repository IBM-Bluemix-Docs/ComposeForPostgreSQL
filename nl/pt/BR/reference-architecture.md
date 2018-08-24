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

# Arquitetura 
{: #architecture}

## Replicação

Um serviço {{site.data.keyword.composeForPostgreSQL_full}} contém um cluster com dois membros de dados; um líder e um membro seguidor. Os dados são replicados em ambos os membros de dados e seu espaço em disco é distribuído pelas zonas de disponibilidade da região.  A alta disponibilidade é gerenciada com Patroni, em que três árbitros etcd mantêm o estado do cluster, gerenciam a replicação e manipulam o failover. Se um membro de dados se tornar inacessível, seu cluster continuará a operar normalmente.

## Criptografia de Disco

Todos os serviços do {{site.data.keyword.composeForPostgreSQL}} têm criptografia em repouso. Seus dados residem em servidores que possuem criptografia em nível de volume ativada. 

Como este {{site.data.keyword.composeForPostgreSQL}} é um serviço gerenciado, é possível que os operadores do {{site.data.keyword.cloud}} Compose vejam dados. Além da criptografia de disco, recomendamos criptografar informações pessoais antes de armazená-las no banco de dados ou usar extensões ou recursos para ativar a criptografia no próprio banco de dados. Embora esses métodos possam afetar a usabilidade ou o desempenho, é uma boa prática assegurar-se de que as informações pessoais sejam protegidas com criptografia.

## Auto-scaling

Os recursos são escalados automaticamente com base no uso total de armazenamento em disco dos bancos de dados PostgreSQL. A memória baseia-se em uma razão de espaço em disco provisionado em 1:4. Esses recursos são empacotados como unidades.

O Auto-scaling foi projetado para responder às tendências de curto a médio prazo de seu banco de dados. A cada hora, seu serviço será verificado e, se ele estiver sendo executado com pouco espaço em disco, mais unidades serão alocadas para a implementação. 

O Auto-scaling não reduz a capacidade de implementações em que o uso de disco/memória foi reduzido. Os recursos provisionados para seus bancos de dados permanecerão para suas necessidades futuras ou até você reduzir a capacidade de sua implementação manualmente.
{: .tip}

## Papéis

Cada serviço PostgreSQL é provisionado com uma função "administrador". Outras funções e permissões podem ser incluídas e gerenciadas por meio de psql. Não há função de "superusuário" para este serviço.

## Extensões do banco de

Use psql para listar, instalar e gerenciar extensões PostgreSQL.

É necessário usar a função "administrador" fornecida para executar os comandos CREATE e ALTER. {: .tip}

### Listando extensões

Use pg_available_extensions para obter uma lista completa de extensões suportadas.
`SELECT name FROM pg_available_extensions;`

### Instalando extensões

Use a extensão CREATE para instalar qualquer extensão.
` CREATE extension <name> ;`

### Atualizando extensões

Use ALTER EXTENSION para instalar uma nova versão de uma extensão.
` ALTER EXTENSION <name> ATUALIZAR TO <version>;`
