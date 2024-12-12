# 3. Trabajando con repositorios remotos

- [Conceptos de repositorios remotos y locales](#conceptos-de-repositorios-remotos-y-locales)
- [Clonar un repositorio remoto](#clonar-un-repositorio-remoto)
- [Conectar y gestionar repositorios remotos](#conectar-y-gestionar-repositorios-remotos)
- [Sincronización de cambios](#sincronización-de-cambios)
- [Ejercicios](#ejercicios)

## Conceptos de repositorios remotos y locales

Uno de los aspectos más poderosos de Git es su capacidad para trabajar de forma distribuida, permitiendo a múltiples personas colaborar en proyectos desde diferentes ubicaciones. Esto se logra mediante la sincronización de repositorios remotos.

Un repositorio remoto es una copia del proyecto almacenada en un servidor que permite a los usuarios compartir cambios y colaborar de manera eficiente.

## Clonar un repositorio remoto

El comando `git clone` crea una copia de un repositorio remoto en tu máquina local.

- **Uso**:
  
  ```bash
  git clone <url-del-repositorio>
  ```

- **Ejemplo**:
  
  ```bash
  git clone https://github.com/usuario/proyecto.git
  ```

## Conectar y gestionar repositorios remotos

Para trabajar con un repositorio remoto, identificado mediante un nombre y la URL de otra máquina que acepta peticiones Git (ya sea por `https` o `ssh`) es necesario configurar Git previamente para conectarlo con dicho remoto.

El caso más habitual es tener un repositorio principal compartido para todo el equipo, que suele recibir el nombre de `origin`:

```bash
git remote add origin <url-remoto>
```

## Sincronización de cambios

Al trabajar con repositorios remotos, los comandos más básicos son `fetch`, `push` y `pull`. Estos comandos permiten sincronizar los cambios entre los repositorios locales y remotos.

### `git fetch`

Descarga todos los cambios del repositorio remoto sin modificar el historial o el estado del directorio de trabajo local. Es útil para obtener actualizaciones sin integrarlas automáticamente.

- **Uso**:
  
  ```bash
  git fetch origin
  ```

  O simplemente:

  ```bash
  git fetch
  ```

### `git push`

Permite enviar los commits locales al repositorio remoto. Esto publica tus cambios para que otros colaboradores puedan acceder a ellos.

- **Uso**:
  
  ```bash
  git push -u origin <nombre-de-la-rama>
  ```

  O simplemente:
  
  ```bash
  git push
  ```

  Si se quiere hacer `push` de una rama que se creó localmente y no existe en remoto:

  ```bash
  git push --set-upstream origin feature
  ```

### `git pull`

Es una combinación de `fetch` y `merge`. Descarga los cambios del repositorio remoto y los fusiona automáticamente con tu rama actual.

- **Uso**:
  
  ```bash
  git pull origin <nombre-de-la-rama>
  ```
  
  O simplemente:

  ```bash
  git pull
  ```

## Ejercicios

1. Clonar el repositorio de `progit` en español.
2. Crear un repositorio remoto con ficheros creados por la plataforma ( `README` y `LICENSE` ) en GitHub y clonarlo en local.
3. Añadir un fichero con algo de texto y sincronizarlo con el repositorio recién clonado.
