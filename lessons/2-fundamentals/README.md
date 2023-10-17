# 2. Conceptos básicos de control de versiones

## Índice

[1. Gestión de cambios](#1-gestión-de-cambios)  
[2. Ramas](#2-ramas)

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

Esto conservará los cambios del fichero. Si se desean eliminar esos cambios se le debe "restaurar" un estado anterior:

    git checkout -- bye.txt

En todo momento es posible saber el estado actual del repositorio:

    git status

O revisar el registro de cambios realizado:

    git log

Para saber las diferencias de los ficheros entre su estado actual y el de la última confirmación, dependiendo de si están en el `stage` o no:

    git diff
    git diff --staged

## 2. Ramas



## Referencias

[La guía sencilla](https://rogerdudler.github.io/git-guide/index.es.html)  
[Tutorial básico](https://www.ionos.es/digitalguide/paginas-web/desarrollo-web/tutorial-de-git/)