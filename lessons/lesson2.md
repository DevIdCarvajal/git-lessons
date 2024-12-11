# 1. Configuración y uso básico de Git
- [Configuración inicial](#configuración-inicial)
- [Creación de un nuevo repositorio Git](#creación-de-un-nuevo-repositorio-Git)
- [Estructura de un repositorio Git](#estructura-de-un-repositorio-Git)
- [Comandos básicos](#cmandos-básicos)
- [Ejercicios](#ejercicios)

## Configuración inicial

- Configurar el nombre de usuario y el correo electrónico es esencial para que Git asocie los cambios con un autor específico:

  ```bash
  git config --global user.name "Tu Nombre"
  git config --global user.email "tuemail@example.com"
  ```
- Verificar la configuración:

  ```bash
  git config --list
  ```

## Creación de un nuevo repositorio Git

1. **Inicialización de un repositorio**: Para comenzar a utilizar Git en un proyecto, debes inicializar un repositorio en la carpeta correspondiente:
    ```bash
    git init
    ```
    Esto crea un directorio oculto llamado `.git`, que contiene todos los archivos necesarios para el control de versiones.

2. **Añadir archivos al repositorio**: Después de inicializar el repositorio, puedes agregar archivos para que Git comience a rastrearlos:
    ```bash
    git add <archivo>
    ```

3. **Confirmar cambios (commit)**: Una vez añadidos los archivos, debes "confirmar" los cambios para que Git los registre en su historial:
    ```bash
    git commit -m "Descripción de los cambios"
    ```

## Estructura de un repositorio Git

El ciclo de vida de los archivos en Git puede entenderse a través de los siguientes estados:

1. **Sin seguimiento (untracked)**: Un archivo que no está siendo rastreado por Git. Es nuevo o ha sido modificado pero no añadido al control de versiones.
   - Comando relevante:
     ```bash
     git status
     ```

2. **Pendiente de confirmación (staged)**: El archivo ha sido modificado y añadido a la *staging* area para su inclusión en el próximo `commit`.
   - Comando relevante:
     ```bash
     git add <archivo>
     ```

3. **Confirmado (committed)**: El archivo ha sido confirmado en el historial de Git, creando una nueva versión en el repositorio.
   - Comando relevante:
     ```bash
     git commit -m "Descripción del cambio"
     ```

## Comandos básicos

- `git add`: Mueve los cambios de archivos al área de staging.
- `git reset`: Saca los cambios de archivos del área de staging.
- `git restore`: Restaura los archivos al estado del último commit, eliminando todos los cambios en el directorio de trabajo.
- `git commit`: Confirma los cambios en el historial.
- `git status`: Muestra el estado del repositorio (qué archivos han cambiado, están listos para ser confirmados, etc.).
- `git log`: Muestra el historial de commits del repositorio.
- `git diff`: Muestra las diferencias entre archivos en distintas versiones o en el área de staging (`diff --staged`).

## Ejercicios

1. Instalar Git y crear un repositorio local para un proyecto llamado `moby-git` .
2. Versionar un cuaderno de bitácora que tenga tres entradas con diferentes contenidos de texto escritas en Markdown, cada una de ellas versionada con un `commit` diferente. En la segunda, además de texto, debe haber una imagen.
3. Comparar el contenido del primer y el tercer `commit` .
