# Migración de Wordpress

En este documento se describen los posibles procesos a la hora de migrar un Wordpress, cuando el dominio o la ruta de acceso a Wordpress se modifique (EJ. Cambio de dominio, cambio de carpeta, montar entorno en local cuando no se puede mantener la misma URL, etc ...)

**IMPORTANTE:** Estos procesos son para migraciones a entornos nuevos (vacios). Par la subida de desarrollos hechos entre entornos de DEV a INT/PRE/PRO, existe otro dodumento concreto en <https://github.com/LSalmeronT/WP_knowledge_base/blob/master/wpcore/Environment_propagation.md>

## Migración con plugin Duplicator

Duplicator es un plugin que nos permite realizar backups de nuestras instancias de wordpress para su migraciòn a nuevos entornos. 

TODO

## Migración manual

En algunos casos es posible que no podamos usar Duplicator, como por ejemplo ante restricciones del servidor que no podemos saltarnos.

En este caso existe un proceso manual que es lo mismo que hace Duplicator internamente.

La migración de archivos se realizará manualmente, bien descargando de SFTP/FTP de origen y subiendo los archivos al destino, o mediante el uso de GIT como "Transportista".

La migración de la BBDD se realizará también manualmente, descargando un DUMP realizado desde consola de MySQL y desde PHPMyAdmin.

Una vez restaurado el dump en la BBDD de destino, será necesario realizar varias sustituciones en la base de datos, para dejar configuradas las nuevas URLs en todos los sitios necesarios:

TODO
