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

# Arquitectura 
{: #architecture}

## Réplica

Un servicio de {{site.data.keyword.composeForPostgreSQL_full}} contiene un clúster con dos miembros de datos: un líder y un miembro seguidor. Los datos se replican en ambos miembros de datos, y su espacio de disco se distribuye por las zonas de disponibilidad de la región.  La alta disponibilidad se gestiona con Patroni, donde tres árbitros de etcd mantienen el estado del clúster, gestionan la replicación y manejan la migración tras error. Si un miembro de datos se vuelve inaccesible, el clúster seguirá funcionando de forma normal.

## Cifrado de disco

Todos los servicios de {{site.data.keyword.composeForPostgreSQL}} tienen cifrado en reposo. Los datos residen en servidores que tienen el cifrado de nivel de volumen habilitado. 

Puesto que {{site.data.keyword.composeForPostgreSQL}} es un servicio gestionado, es posible que los operadores de {{site.data.keyword.cloud}} Compose vean los datos. Además del cifrado de disco, le recomendamos que cifre la información personal antes de almacenarla en la base de datos o que utilice extensiones o funciones para habilitar el cifrado en la propia base de datos. Si bien estos métodos pueden afectar a la usabilidad o al rendimiento, es una buena práctica asegurarse de que la información personal esté protegida con cifrado.

## Escalado automático

Los recursos se escalan automáticamente basándose en el uso de almacenamiento de disco total de las bases de datos PostgreSQL. La memoria se basa en una proporción de espacio de disco suministrado de 1:4. Estos recursos se empaquetan como unidades.

El escalado automático está diseñado para responder a las tendencias a corto y medio plazo de la base de datos. Cada hora, el servicio está marcado y si se está quedando corto en el espacio de disco, se asignan más unidades al despliegue. 

El escalado automático no reduce los despliegues en los que el uso de disco/memoria se ha reducido. Los recursos suministrados a las bases de datos permanecerán para sus necesidades futuras, o hasta que reduzca el despliegue manualmente.
{: .tip}

## Roles

Todos los servicios PostgreSQL se suministran con un rol "admin". Otros roles y permisos se pueden añadir y gestionar a través de psql. No hay rol de "superusuario" para este servicio.

## Extensiones de base de datos

Utilice psql para listar, instalar y gestionar las extensiones PostgreSQL.

Debe utilizar el rol "admin" proporcionado para ejecutar los mandatos CREATE y ALTER. {: .tip}

### Listado de extensiones

Utilice pg_available_extensions para obtener una lista completa de las extensiones soportadas.
`SELECT name FROM pg_available_extensions;`

### Instalación de extensiones

Utilice la extensión CREATE para instalar cualquier extensión.
`CREATE extension <name> ;`

### Actualización de extensiones

Utilice ALTER EXTENSION para instalar una nueva versión de una extensión.
`ALTER EXTENSION <name> UPDATE TO <version>;`
