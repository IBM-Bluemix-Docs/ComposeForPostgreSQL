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

# Conexión de una aplicación externa
{: #connecting-external-app}

Hay dos formas de conectar una aplicación externa a {{site.data.keyword.composeForPostgreSQL_full}}:

- Algunas bibliotecas de cliente pueden utilizar una **serie de conexión**, que contiene toda la información necesaria para que se conecten otras bibliotecas.

- La **línea de mandatos** es un mandato preformateado que invocará `psql` con los parámetros correctos.

Encontrará ambas en la página *Visión general* del servicio {{site.data.keyword.composeForPostgreSQL}}.

## Conexión con un controlador de un lenguaje

Postgres tiene una amplia gama de controladores de lenguajes.  La tabla incluye algunos de los más comunes.

Lenguaje|Ejemplos
----------|-----------
PHP|[pgsql](http://php.net/manual/en/pgsql.examples-basic.php)
Ruby|[ruby-pg](https://bitbucket.org/ged/ruby-pg/wiki/Home)
Ruby on Rails|[Rails guide](http://edgeguides.rubyonrails.org/configuring.html#configuring-a-postgresql-database)
Python|[Psycopg2](https://wiki.postgresql.org/wiki/Psycopg2_Tutorial)
C#|[ODBC](https://wiki.postgresql.org/wiki/Using_Microsoft_.NET_with_the_PostgreSQL_Database_Server_via_ODBC)
Go|[pq](https://godoc.org/github.com/lib/pq)
Node|[node-postgres](https://github.com/brianc/node-postgres/wiki/Example)

## Conexión con la línea de mandatos

**psql** es la herramienta de línea de mandatos para conectar con Postgres. Para poderlas utilizar, las herramientas de cliente de PostgreSQL deben estar instaladas en el sistema local. Se pueden instalar mediante la instalación del paquete de PostgreSQL completo descargado desde postgresql.org, desde los paquetes de sistema operativos o, en MacOS X con brew instalado, mediante la ejecución de `brew install postgresql`).   

Encontrará más información sobre psql en la documentación de PostgreSQL - [consulta](https://www.postgresql.org/docs/current/static/app-psql.html) - y una breve [introducción](http://postgresguide.com/utilities/psql.html) en la Guía de Postgres.

Encontrará el mandato de línea de mandatos que debe utilizar en el panel de control de la instancia de {{site.data.keyword.composeForPostgreSQL}}, en el separador Visión general.

```
psql "sslmode=require host=bluemix-sandbox-dal-9-portal.6.dblayer.com port=24761 dbname=compose user=admin"
```

Cuando escriba el mandato, se le solicitará la contraseña, que encontrará en la información sobre series de conexión en el mismo separador o en las *Credenciales de servicio*.

## Conexión con pgAdmin3

pgAdmin3 es un cliente de GUI muy utilizado para PostgreSQL. Siga los pasos siguientes para conectar con pgAdmin 3

1. Descargue e instale la versión de pgAdmin3 para su sistema operativo desde [https://www.pgadmin.org/](https://www.pgadmin.org/).
2. Ejecute pgAdmin3 y seleccione "Añadir servidor" en la barra de menús para crear una nueva conexión para abrir el panel *Nuevo registro de servidor*.

  ![Nuevo registro de servidor de pgAdmin3. Separador Propiedades.](./images/pgadmin.png "El separador de propiedades del panel Nuevo registro de servidor de pgAdmin3.")

3. Complete los campos del panel con la información de la página Visión general del servicio {{site.data.keyword.composeForPostgreSQL}}:

  * **Nombre**: puede ser cualquiera que describa el despliegue de Postgres.  Para simplificar, especifique el nombre que ha utilizado en Compose.
  * **Host**: la parte de host de la serie de conexión.
  * **Puerto**: la parte de puerto de la serie de conexión.
  * **Nombre de usuario**: el nombre de usuario del administrador o de un usuario que haya creado.
  * **Contraseña**: la contraseña del administrador (que encontrará en la sección Credenciales) o de un usuario que haya creado.

4. Después de completar los campos, seleccione el separador "SSL":

  ![Panel Nuevo registro de servidor de pgAdmin3. Separador SSL.](./images/pgadmin_ssl.png "El separador SSL del panel Nuevo registro de usuario de pgAdmin3.")

5. Cambie SSL por "require".
6. Pulse "Aceptar" para guardar los valores de conexión y conectar con la base de datos.
