# 2. Trabajo en local

## Índice

[1. Gestión de cambios](#1-gestión-de-cambios)  
[2. Ramas](#2-ramas)  
[3. Etiquetas](#3-etiquetas)

## 1. Gestión de cambios

El primer paso para trabajar con Git es tener una carpeta que contendrá todo el contenido del proyecto a versionar y estando dentro de ella, inicializar un repositorio Git:

    mkdir miCarpeta
    cd rutaDeMiCarpeta

    git init

Esto crea una carpeta oculta `.git` donde se guardan todas las operaciones realizadas en el control de versiones.

Es importante entender que Git guarda los **cambios** realizados en los ficheros y carpetas del proyecto, sean estos de creación, modificación o borrado.

Para ello, dichos cambios se añaden al `stage`, que es un estado previo a la confirmación de los mismos para una versión concreta del proyecto:

    echo "Hola mundo" > hello.txt
    
    git add .

El siguiente paso es por tanto confirmar esos cambios, lo que llevará un mensaje asociado para reconocer dicha confirmación en un futuro:

    git commit -m "Mi primer commit"

Cada vez que se quiera hay que generar un commit debe hacerse siguiendo esos dos pasos: primero añadir al `stage` y después confirmar.

Si por error se añaden ficheros al `stage` o simplemente se desean sacar del mismo para que no estén en la siguiente confirmación, se puede hacer con:

    echo "Adiós mundo" > bye.txt
    
    git add .

    git reset bye.txt

Si lo que se pretende es que un fichero deje de ser completamente versionado por Git pero conservándose en la carpeta de trabajo (es decir, sea ignorado), se debe usar este otro comando:

    git rm --cached bye.txt

Esto conservará los cambios del fichero. Si se desean eliminar esos cambios se le debe "restaurar" un estado anterior:

    git checkout bye.txt

O alternativamente, desde la versión 2.23 de Git (2019):

    git restore bye.txt

En todo momento es posible saber el estado actual del repositorio:

    git status

O revisar el registro de cambios realizado:

    git log

Para saber las diferencias de los ficheros entre su estado actual y el de la última confirmación, dependiendo de si no fueron añadidos al `stage` o sí, respectivamente:

    git diff
    git diff --staged

## 2. Ramas

Git permite la creación de ramas para crear líneas alternativas de desarrollo, de forma que los cambios de una rama no afecten al de la otra.

Cada una tiene su propia área de `stage` y sus propios `commits`, quedando totalmente aisladas unas de otras.

Para crear una rama se puede hacer de la siguiente manera:

    git branch nuevaRama

Para ver tanto las ramas creadas como la rama en la que se está trabajando actualmente:

    git branch

Para cambiar de una rama a otra:

    git checkout nuevaRama

Como forma abreviada y más rápida de crear una rama y cambiar a esta en una operación:

    git checkout -b nuevaRama

Para eliminar una rama se puede hacer con:

    git branch -d nuevaRama

Al cambiar de rama se debe tener en cuenta que los cambios en la rama que se deja se perderán, salvo que se haga previamente un `commit` de los mismos.

Otra opción recomendada para no perder dichos cambios de la rama dejada es guardarlos en un espacio temporal:

    git stash

Para que al volver a la rama se recuperen los cambios añadidos en el espacio de `stash` se puede hacer con:

    git stash pop

Lo que elimina los cambios del `stash`. Si se desean aplicar sin que estos se eliminen, sería de esta forma:

    git stash apply

Por otro lado, los `commits` realizados en una rama (e.g., `nuevaRama`) pueden aplicarse a otra (e.g., `master`), haciendo:

    git checkout master

    git merge nuevaRama

Es decir, es necesario cambiarse a la rama que recibe los cambios y una vez estando en ella se le aplican los cambios de la otra rama.

En algunos casos, cuando los cambios afectan a las mismas partes de los ficheros implicados, si estos son diferentes se originará un conflicto, que habrá que resolver manualmente en esos ficheros, para posteriormente hacer otro `commit` con las decisiones tomadas en la resolución.

## 3. Etiquetas

Es posible generar referencias a `commits` concretos conocidas como etiquetas, algo que generalmente se usa para identificar versiones del proyecto, de cara a su publicación.

Estas etiquetas son similares a las ramas, salvo por el hecho de que no pueden cambiar, esto es, no se pueden hacer más `commits` sobre ellas.

Para crear una etiqueta anotada (con todos los metadatos de autor, correo y fecha) con un mensaje asociado en el `commit` actual:

    git tag -a v0.5 -m "Alpha version"

O también como una etiqueta ligera (sin metadatos ni mensaje):

    git tag v0.5.1

Para etiquetar otro `commit` se indica el *hash* del mismo previamente localizado con `git log`:

    git tag -a v0.2 15027957951b64cf874c3557a0f3547bd83b3ff6

Para ver el estado del repositorio tal como se quedó cuando se le creó una etiqueta:

    git checkout v0.5

Se pueden ver las etiquetas creadas:

    git tag

Y borrarlas por su nombre:

    git tag -d v0.5

## Referencias

[La guía sencilla](https://rogerdudler.github.io/git-guide/index.es.html)  
[Tutorial básico](https://www.ionos.es/digitalguide/paginas-web/desarrollo-web/tutorial-de-git/)  
[Guardar cambios](https://www.atlassian.com/es/git/tutorials/saving-changes)  
[Etiquetado](https://www.atlassian.com/es/git/tutorials/inspecting-a-repository/git-tag)