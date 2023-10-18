# 3. Trabajo en remoto

## Índice

[1. Comunicación con servidor](#1-comunicación-con-servidor)  
[2. Plataformas de desarrollo](#2-plataformas-de-desarrollo)

## 1. Comunicación con servidor

Cuando se desea trabajar con un servidor remoto de Git, existen dos escenarios posibles:

- El proyecto ha sido inicializado localmente, tiene al menos un `commit` y no hay nada en el servidor.
- No hay nada localmente y el proyecto se encuentra en el servidor con al menos un `commit`.

Para el primer caso, se debe asociar el repositorio Git local a un servidor Git remoto mediante:

    git remote add origin urlRepositorio

Para el segundo caso, se debe clonar (el equivalente a descargar una copia idéntica) el repositorio remoto al entorno local:

    git clone urlRepositorio

En cualquiera de los dos casos, Git enlaza un repositorio local con uno remoto, de manera que es posible actualizar los últimos cambios del servidor:

    git pull

Subir los cambios locales al servidor tras hacer un commit:

    git push

O ver los cambios sin aplicarlos:

    git fetch

### Resumen del flujo de trabajo completo

![Flujo de trabajo](workflow.png)

### Trazabilidad y auditoría

Además de revisar el registro de commits con `git log` o con las etiquetas anotadas, que también guardan información sobre la autoría de los cambios y las versiones del proyecto, existe otro comando específicamente pensado para cuestiones de trazabilidad:

    git blame hello.txt

Este comando tiene varios opciones disponibles como ignorar cambios por espacios en blanco (`-w`), mostrar el email de los autores (`-e`), o líneas copiadas o movidas dentro del fichero (`-M`) o desde otros ficheros (`-C`).

## 2. Plataformas de desarrollo colaborativas

### BitBucket

.

### GitHub

.

### GitLab

.

## Referencias

[Tutorial completo](https://www.diegocmartin.com/tutorial-git/)  
[Sincronización](https://www.atlassian.com/es/git/tutorials/syncing)