# Trabajar con GIT y GIT FLOW

En este documento se describe la forma correcta de trabajar en los proyectos de cara a GIT, y mas concretamente, a la metodología GITFLOW.

## Features

Un feature es una nueva rama sobre la que se desarrollará una funcionalidad o conjunto de funcionalidades, y que al finalizar, serán añadidos a la rama **develop**

### Inicio de desarrollo de una nueva historia

Se obtiene la última versión de la rama develop:

- **git checkout develop && git pull**

Se crea la historia XXX con Git Flow:

- **git flow feature start FEATURE_UNIQ_NAME**
Git ya queda posicionado en la nueva rama y se comienza el desarrollo del feature.

### Subida de feature a GIT

Si necesitamos subir nuestra rama feature a remoto, por ejemplo para hacer un backup en remoto de nuestro repositorio local, compartir los avances con un compañero, o como medio para luego publicar dicho feature en un entorno de testeo o integración, es necesario ejecutar la primera vez el siguiente comando:

- **git push --set-upstream origin FEATURE_UNIQ_NAME**

A partir de esa primera subida, solo será necesario usar el siguiente comando para ir actualziando el repositorio remoto con nuestros cambios:

- **git push**

### Fin del desarrollo

Una vez hemos finalizado el desarrollo que ibamos a incluir en nuestro feature, es necesario cerrarlo con el siguiente comando:

- **git flow feature finishXXX**

Con este último comando, se hace el merge de la rama a develop y se borra el feature. Para subir los cambios en develop a la rama develop remota:

- **git push origin develop**

RELEASES    Creación de la Release   Obtener las últimas versiones de master y develop  o git checkout master && git pull  o git checkout develop && git pull   Cuando se quieren desplegar las features añadidas a develop desde la última release, se verifica cuál es el último tag creado y se le suma uno al segundo dígito y con el tercer dígito en 0.  Ejemplo: SI el último tag es 2.1.1, se creará la release con el número 2.2.0  o git flow release start x.x.x   o Con el comando anterior, Git Flow crea una rama de release llamada release/x.x.x partiendo de la punta de develop. Esta es la última oportunidad para modificar la codebase antes del merge a master y hacer commits que no sean específicos de una feature concreta pero necesarios para la release.     Finalización de la Release  o Cuando la release está lista para ser desplegada  o git flow release finish x.x.x  
o Con el comando anterio, Git Flow hace merge de la rama release/x.x.x a master y develop, crea el tag de release x.x.x en el commit del merge a master y borra la rama de release  o Validar que los últimos commits de master y develop son los mismos  o git checkout master && git log   o git checkout develop && git log  o En caso de haber algún commit diferente, hacer el merge correspondiente. Por ejemplo si falta un commit de develop en master, hacer  o git checkout master && git merge develop   o En caso de ser al revés:  o git checkout develop && git merge master  o Se suben los últimos cambios a remoto  o git push origin develop  o git push origin master  o Publicar el tag  o git push --tags    
 
 
HOTFIXES    Inicio de desarrollo de una corrección   Obtener la última versión de master  o git checkout master && git pull   Se verifica cuál es el tag de la release que de la que debemos hacer el hotfix, y se le incrementa en uno el último digito  Ejemplo: SI la release es la 2.3.0, se creará el hotfix con el número 2.3.1 (si no existe ya ese tag)  o git flow hotfix start x.x.x    Se comienza el desarrollo en la rama hotfix/x.x.x que git-flow ha creado partiendo de la punta de master (que debería ser también le commit de la última release).     Fin de desarrollo de la corrección   Cuando el código de la corrección está listo para ser desplegado, se hace  o git flow hotfix finish x.x.x   Con este último comando, Git Flow hace el merge de la rama hotfix/x.x.x a master y develop, crea el tag de release x.x.x en el commit del merge a master y borra la rama de hotfix   Validar que los últimos commits de master y develop son los mismos (de la misma manera que para las releases)  o git checkout master && git log   o git checkout develop && git log   En caso de haber algún commit diferente, hacer el merge correspondiente. Por ejemplo si falta un commit de develop en master, hacer  o git checkout master && git merge develop   Se suben los úlgit cotimos cambios a remoto  o git push origin develop  o git push origin master   Publicar el tag  o Git push --tags  