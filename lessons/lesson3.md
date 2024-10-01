# 3. Herramientas gráficas y comandos avanzados

- [Ejemplos de herramientas](#ejemplos-de-herramientas)
- [Cherry-picking y otros comandos avanzados](#cherry-picking-y-otros-comandos-avanzados)
- [Ejercicios](#ejercicios)

## Ejemplos de herramientas

Aunque Git es extremadamente poderoso desde la línea de comandos, existen varias herramientas gráficas que pueden facilitar su uso, especialmente en proyectos complejos o en equipos grandes. Estas herramientas ofrecen interfaces visuales intuitivas para manejar commits, ramas, fusiones, y otros aspectos de Git.

### 1. Gitk

Gitk es una de las herramientas gráficas más básicas, pero efectivas, que viene con Git. Ofrece una interfaz visual para explorar el historial de commits en un formato de árbol.

- **Características**:
  - Ver la historia de commits de manera gráfica.
  - Ver los cambios en archivos entre commits.
  - Navegar entre ramas y etiquetas.
  
- **Cómo usarlo**: Simplemente ejecuta `gitk` en el terminal desde el directorio del repositorio:
  ```bash
  gitk
  ```
  Esto abrirá una ventana que mostrará el historial de commits en forma de gráfico.

### 2. DiffMerge

DiffMerge es una herramienta multiplataforma que ayuda a comparar y fusionar archivos.

- **Características**:
  - Comparación de archivos y carpetas.
  - Fusión de conflictos de fusión en Git.
  - Integración con Git para comparar y fusionar cambios entre ramas.

- **Uso en Git**: Puedes configurar DiffMerge como tu herramienta de comparación o fusión en Git:
  ```bash
  git config --global diff.tool diffmerge
  git config --global merge.tool diffmerge
  ```

### 3. SmartGit

SmartGit es una herramienta gráfica avanzada que soporta múltiples sistemas de control de versiones (Git, SVN, etc.) y es una de las más populares en entornos empresariales.

- **Características**:
  - Interfaz visual amigable para Git.
  - Administración de repositorios locales y remotos.
  - Soporte para flujos de trabajo complejos con ramas.
  - Integración con GitHub, Bitbucket, GitLab, etc.

- **Ventajas**:
  - Compatible con flujos de trabajo Git avanzados.
  - Ofrece una vista clara de las diferencias, fusiones y conflictos.

### 4. GitKraken

GitKraken es una herramienta gráfica de Git orientada a facilitar la colaboración y la gestión de proyectos Git, con una interfaz moderna y visual.

- **Características**:
  - Visualización avanzada de ramas y commits.
  - Integración con GitHub, GitLab y Bitbucket.
  - Fácil manejo de fusiones y conflictos.
  - Soporte para GitFlow y otros flujos de trabajo.

- **Ventajas**:
  - Interfaz limpia y fácil de usar.
  - Buen soporte para operaciones avanzadas de Git como `rebase` y `cherry-pick`.

### 5. SourceTree

SourceTree es una herramienta gratuita para Git desarrollada por Atlassian, conocida por su integración nativa con Bitbucket, pero también soporta GitHub y GitLab.

- **Características**:
  - Interfaz gráfica simple para Git.
  - Gestión avanzada de repositorios y ramas.
  - Soporte para flujos de trabajo como GitFlow.
  - Buenas herramientas para la visualización de diferencias y fusiones.

- **Ventajas**:
  - Ideal para principiantes y usuarios intermedios.
  - Buena integración con plataformas populares de alojamiento de repositorios.

## Cherry-picking y otros comandos avanzados

Git no solo proporciona comandos básicos, sino que también cuenta con una serie de comandos avanzados que permiten un control más granular sobre los commits, la historia, y la limpieza del repositorio.

### 1. `cherry-pick`

El comando `git cherry-pick` permite aplicar un commit específico de otra rama o del historial a la rama actual, sin necesidad de fusionar ramas completas.

- **Uso típico**: Supongamos que tienes un commit en la rama `feature` que deseas aplicar a `main` sin fusionar toda la rama:
  ```bash
  git checkout main
  git cherry-pick <commit-hash>
  ```

- **Ventajas**:
  - Te permite traer commits específicos sin mezclar el historial completo.
  - Útil en casos donde solo se necesita aplicar ciertos cambios.

### 2. `rev-parse`

`git rev-parse` es un comando poco conocido, pero muy útil. Se utiliza para transformar referencias simbólicas como ramas, tags, y nombres de commit en hashes de commit SHA-1.

- **Ejemplos de uso**:
  1. Obtener el hash de commit de la rama actual:
     ```bash
     git rev-parse HEAD
     ```
  2. Convertir una referencia simbólica a su hash:
     ```bash
     git rev-parse master
     ```

### 3. `amend`

`git commit --amend` permite modificar el último commit. Es útil si olvidaste añadir algo al commit anterior o cometiste un error en el mensaje de commit.

- **Uso típico**: Después de hacer un commit, si olvidas añadir un archivo, puedes hacer lo siguiente:
  ```bash
  git add archivo_olvidado
  git commit --amend
  ```
  Esto actualizará el último commit en lugar de crear uno nuevo.

- **Advertencia**: No uses `amend` en commits que ya hayan sido empujados a un repositorio remoto, ya que cambiará el historial de commits.

### 4. `clean`

`git clean` se utiliza para eliminar archivos no rastreados en tu directorio de trabajo.

- **Uso básico**: Si has acumulado archivos temporales o archivos generados que no forman parte del repositorio y deseas eliminarlos:
  ```bash
  git clean -f
  ```
  
- **Advertencia**: Ten cuidado al usar este comando, ya que eliminará archivos permanentemente si no están siendo rastreados por Git.

### 5. `revert`

`git revert` es una manera segura de deshacer cambios en el historial sin reescribir el historial de commits. A diferencia de `reset`, que puede eliminar commits, `revert` crea un nuevo commit que invierte los cambios del commit especificado.

- **Uso típico**: Si deseas deshacer un commit específico sin modificar el historial de la rama:
  ```bash
  git revert <commit-hash>
  ```

- **Ventajas**:
  - Mantiene el historial intacto.
  - Ideal en situaciones donde se trabaja en equipo y los commits ya han sido compartidos.

### 6. `rebase`

El comando `git rebase` es un comando avanzado que permite reorganizar los commits aplicándolos sobre otro commit base. Se utiliza para limpiar el historial y crear una secuencia de commits más lineal y comprensible.

- **Rebase interactivo**: Un uso poderoso de `rebase` es el rebase interactivo, que te permite modificar, reordenar o eliminar commits.
  ```bash
  git rebase -i HEAD~3
  ```
  Esto abrirá una interfaz que te permitirá modificar los últimos tres commits.

- **Ventajas**:
  - Limpia el historial de commits, eliminando commits innecesarios o reescribiéndolos.
  - Útil para proyectos donde se prefiere un historial lineal.

- **Advertencia**: Al igual que `amend`, debes evitar hacer un `rebase` en commits que ya hayan sido empujados a un repositorio remoto, ya que puede causar problemas para otros desarrolladores.

## Ejercicios

1. Instalar Gitk, DiffMerge, SmartGit, GitKraken y SourceTree y explorar las distintas herramientas para realizar y entender las operaciones básicas vistas hasta ahora: `commits`, `tags`, `diffs`, ramas, etc.
2. Hacer `cherry-picking` desde un `commit` de una rama a otro `commit` de otra rama.
3. Usar al menos una vez cada uno de los otros comandos avanzados vistos hasta ahora. Por cada uso, hacer los `diffs` necesarios para entender lo que cada comando hace exactamente.