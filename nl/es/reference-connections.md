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

# Configuración de conexión
{: #connection-configuration}

Las conexiones de base de datos {{site.data.keyword.composeForPostgreSQL_full}} están gestionadas por 2 portales HAProxy. Cada portal tiene 64 MB de memoria. El hecho de tener dos portales permite que las aplicaciones mantengan la conectividad si uno de los portales pasa a ser inaccesible.

La migración tras error en el lado del cliente es responsabilidad del diseñador de aplicaciones. Algunos controladores PostgreSQL manejan varias series de conexión y una migración tras error ordenada automáticamente. A menos que esté trabajando con un controlador que gestione por completo los errores de migración tras error, debe:

* Utilizar un controlador que acepte varios puntos finales en su configuración de conexión.
* Asegurarse de que las llamadas de aplicaciones para leer o escribir en la base de datos reaccionen a los errores adecuadamente. Entre las opciones, se incluyen:
  + Registrar el error y reconectar.
  + Reconectar y reintentar la operación que ha provocado el error.
  + Poner en cola la operación que ha fallado y planificar la reconexión.

## Cifrado en tránsito

Todos los portales HAProxy de {{site.data.keyword.composeForPostgreSQL}} tienen habilitado TLS/SSL y dan soporte a TLS versión 1.2. Los certificados para el servicio son certificados autofirmados. Es posible que tenga que guardar una copia local del certificado para el servicio y proporcionar su ubicación a su controlador de aplicaciones para poder realizar una conexión segura.

## Límites de conexión

Las conexiones de base de datos tienen un límite de conexión inicial de 100 conexiones para el servicio. Dependiendo de los recursos que asigne al servicio mediante el escalado automático o manual, el límite de conexiones estará en 1000 conexiones. El exceso del límite de conexión hará que el servicio no responda.

Puede gestionar las conexiones desde la aplicación a través de la característica de agrupación de conexiones del controlador.
{: .tip}

## Tiempos de espera del proxy

Los portales HAProxy gestionan el ciclo de vida de las conexiones entre el servidor y el cliente. Los detallamos aquí como una referencia para los escritores de controladores y otros que tienen interés en la actividad de bajo nivel de las conexiones de base de datos de {{site.data.keyword.composeForPostgreSQL}}.

Valor | Valor | Se aplica
----------|-----------|-----------
cliente | 1 día | Cuando se espera que el cliente reconozca o envíe datos.
connect | 4s | Cuando se realiza una conexión entre el proxy y el servidor.
servidor | 30m | Cuando se espera que el servidor reconozca o envíe datos.
tunnel | 1d | Cuando se establece una conexión bidireccional entre un cliente y un servidor, y la conexión permanece inactiva en ambas direcciones.
client-fin | 5m | Cuando se espera que el cliente reconozca o envíe datos mientras una dirección ya está cerrada.
check | 5s | Como una comprobación de tiempo de espera secundaria, cuando se realiza una conexión entre el proxy y el servidor.

{: caption="Tabla 1. Tiempos de espera de HAProxy de PostgreSQL" caption-side="top"}
