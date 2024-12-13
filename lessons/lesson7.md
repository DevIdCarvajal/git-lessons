# 7. Trabajo avanzado con Git

- [Reescribir historial de commits](#reescribir-historial-de-commits)
- [Cherry-pick de commits específicos](#cherry-pick-de-commits-específicos)
- [Manejo de submódulos en proyectos grandes](#manejo-de-submódulos-en-proyectos-grandes)
- [Etiquetado de versiones](#etiquetado-de-versiones)

## Reescribir historial de commits

### `git commit --amend`

Esta opción permite modificar el último commit. Es útil si olvidaste añadir algo al commit anterior o cometiste un error en el mensaje de commit.

- **Uso típico**: Después de hacer un commit, si olvidas añadir un archivo, puedes hacer lo siguiente:
  ```bash
  git add archivo_olvidado
  git commit --amend
  ```
  Esto actualizará el último commit en lugar de crear uno nuevo.

- **Advertencia**: No uses `amend` en commits que ya hayan sido empujados a un repositorio remoto, ya que cambiará el historial de commits.

### `git rebase`

Es un comando avanzado que permite reorganizar los commits aplicándolos sobre otro commit base. Se utiliza para limpiar el historial y crear una secuencia de commits más lineal y comprensible.

- **Uso típico**: Si estás trabajando en una rama `feature` y quieres incorporar los últimos cambios de `main`, puedes hacer lo siguiente:
  ```bash
  git checkout feature
  git rebase main
  ```
  Esto moverá los commits de `feature` sobre la rama `main`, creando un historial lineal en lugar de fusionar con un commit de merge.

- **Rebase interactivo**: Un uso poderoso de `rebase` es el rebase interactivo, que te permite modificar, reordenar o eliminar commits.
  ```bash
  git rebase -i HEAD~3
  ```
  Esto abrirá una interfaz que te permitirá modificar los últimos tres commits.

- **Ventajas**:
  - Limpia el historial de commits, eliminando commits innecesarios o reescribiéndolos.
  - Útil para proyectos donde se prefiere un historial lineal.

- **Advertencia**: Al igual que `amend`, debes evitar hacer un `rebase` en commits que ya hayan sido empujados a un repositorio remoto, ya que puede causar problemas para otros desarrolladores.

## Cherry-pick de commits específicos

El comando `git cherry-pick` permite aplicar un commit específico de otra rama o del historial a la rama actual, sin necesidad de fusionar ramas completas.

- **Uso típico**: Supongamos que tienes un commit en la rama `feature` que deseas aplicar a `main` sin fusionar toda la rama:
  ```bash
  git checkout main
  git cherry-pick <commit-hash>
  ```

- **Ventajas**:
  - Te permite traer commits específicos sin mezclar el historial completo.
  - Útil en casos donde solo se necesita aplicar ciertos cambios.

## Manejo de submódulos en proyectos grandes

Los submódulos de Git son la forma de incluir un repositorio dentro de otro, pudiendo gestionar ambos por separado, lo que permite poder crear proyectos que se apoyen por ejemplo en librerías que están siendo mantenidas por otro equipo.

- **Añadir un módulo a un repositorio**: Si deseas crear un submódulo dentro de otro repositorio:
  
  ```bash
  git submodule add <url-del-repositorio> <subcarpeta>
  ```
  Esto genera un fichero `.gitmodules` en el que se listan todos los módulos que se han añadido.

- **Clonar un repositorio con submódulos**: En estos casos, las ubicaciones que contienen los módulos están vacías, por lo que hay que activarlos y descargar su contenido:
  
  ```bash
  git submodule init
  git submodule update
  ```

- **Eliminar un módulo**: En lugar de hacerlo mediante un comando específico, se puede hacer de diversas formas:
  
  1. Eliminar la información sobre el módulo en el archivo `.gitmodules`.
  2. Eliminar la información sobre el módulo en el archivo `.git/config`.
  3. Eliminar la ubicación asociada al módulo:
  
      ```bash
      git rm --cached <subcarpeta>
      ```

- **Actualizar un módulo**: Los submódulos deben actualizarse por separado y de manera independiente al repositorio principal. Para ello, desde la ubicación asociada al módulo se debe seleccionar la rama adecuada y actualizar de remoto:
  
  ```bash
  cd <subcarpeta>
  git status
  git checkout main
  git pull
  ```

## Etiquetado de versiones

Las **etiquetas** o **tags** en Git son marcadores que se utilizan para señalar puntos específicos en la historia del proyecto, como lanzamientos de versiones importantes o hitos clave. A diferencia de los commits, las etiquetas son inmutables, es decir, no cambian una vez creadas.

- **¿Por qué usar tags?**: Los tags son útiles para identificar versiones específicas de tu proyecto, como una versión de producción estable. En equipos, es común que se use una etiqueta para señalar la versión que ha sido lanzada.

- **Tipos de etiquetas en Git**:
  1. **Ligeras**: Simplemente una referencia a un commit.
     ```bash
     git tag v0.5
     ```
  2. **Anotadas**: Estas contienen más información, como el nombre del autor, fecha y un mensaje.
     ```bash
     git tag -a v1.0 -m "Production version v1.0"
     ```

- **Ver todas las etiquetas**: Para ver una lista de todas las etiquetas creadas en tu repositorio:
  ```bash
  git tag
  ```

- **Ver el detalle de etiquetas anotadas**: Para ver el mensaje y otros datos de una etiqueta anotada:
  ```bash
  git show v1.0
  ```

- **Publicar etiquetas en un repositorio remoto**: Después de crear una etiqueta, es necesario enviarla al repositorio remoto:
  ```bash
  git push origin v1.0
  ```

- **Eliminar una etiqueta**: Si deseas eliminar una etiqueta localmente y en el remoto:
  ```bash
  git tag -d v1.0
  git push origin :refs/tags/v1.0
  ```
