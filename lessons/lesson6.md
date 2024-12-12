# 6. Historial y deshacer cambios

- [Inspección del historial de cambios](#inspección-del-historial-de-cambios)
- [Revertir cambios](#revertir-cambios)
- [Creación de commits atómicos y limpios](#creación-de-commits-atómicos-y-limpios)
- [Uso de stash para guardar cambios temporales](#uso-de-stash-para-guardar-cambios-temporales)
- [Ejercicios](#ejercicios)

## Inspección del historial de cambios

[git log, git diff]

## Revertir cambios

### `git checkout`

[...]

### `git reset`

Es un comando que permite mover el puntero `HEAD` a un commit específico y cambiar el estado de los archivos en el área de trabajo. Existen cinco modos de `reset`, pero los más usados son los modos `--soft` y `--hard`.

- **--soft**: Mueve el puntero `HEAD` al commit especificado, pero mantiene los cambios en el área de staging. Es útil cuando quieres rehacer los commits sin perder tus cambios.
  ```bash
  git reset --soft HEAD~1
  ```
  Esto deshace el último commit, pero mantiene los cambios en el área de staging, permitiéndote hacer un nuevo commit después.

- **--mixed** (por defecto): Mueve el puntero `HEAD` al commit especificado y deshace los cambios en el área de staging, pero deja intactos los archivos modificados en tu directorio de trabajo.
- **--hard**: Mueve el puntero `HEAD` al commit especificado y deshace todos los cambios tanto en el área de staging como en el directorio de trabajo. Es irreversible, por lo que debes usarlo con precaución.
  ```bash
  git reset --hard HEAD~1
  ```
  Esto deshace el último commit y borra todos los cambios no comprometidos del área de staging y del directorio de trabajo.
- **--merge** y **--keep**: Son opciones avanzadas que se utilizan para conservar o descartar cambios no fusionados durante el proceso de reset.

### `git revert`

Es una manera segura de deshacer cambios en el historial sin reescribir el historial de commits. A diferencia de `reset`, que puede eliminar commits, `revert` crea un nuevo commit que invierte los cambios del commit especificado.

- **Uso típico**: Si deseas deshacer un commit específico sin modificar el historial de la rama:
  ```bash
  git revert <commit-hash>
  ```

- **Ventajas**:
  - Mantiene el historial intacto.
  - Ideal en situaciones donde se trabaja en equipo y los commits ya han sido compartidos.

## Creación de commits atómicos y limpios

[...]

## Uso de stash para guardar cambios temporales

Git permite **guardar temporalmente** los cambios no confirmados utilizando el comando `git stash`. Esto es útil cuando necesitas cambiar de rama o trabajar en una tarea urgente sin perder el progreso de lo que estabas haciendo.

- **¿Qué hace `git stash`?**: Guarda tus cambios en una pila temporal, permitiéndote aplicar esos cambios más adelante. Imagina que estás trabajando en una característica y surge un bug urgente en otra rama. Puedes guardar temporalmente tus cambios actuales, cambiar de rama, arreglar el bug, y luego retomar donde lo dejaste.

- **Cómo usar `stash`**:
  1. **Guardar los cambios**:
     ```bash
     git stash
     ```
     Esto guarda los cambios no confirmados y devuelve tu directorio de trabajo a un estado limpio.
     
  2. **Listar los cambios almacenados**: Para ver las diferentes entradas en el stash:
     ```bash
     git stash list
     ```

  3. **Recuperar los cambios guardados manteniéndolos también en la pila**: Puedes aplicar los cambios guardados en cualquier momento, sin que estos desaparezcan de la pila:
     ```bash
     git stash apply
     ```
     Si tienes más de un stash guardado, puedes especificar cuál aplicar usando el índice:
     ```bash
     git stash apply stash@{2}
     ```

  4. **Recuperar los últimos cambios guardados sacándolos de la pila**: También puedes aplicar los cambios que se guardaron en último lugar, haciendo que estos desaparezcan de la pila:
     ```bash
     git stash pop
     ```

  5. **Eliminar un stash**: Una vez aplicados los cambios, puedes eliminar el stash correspondiente:
     ```bash
     git stash drop stash@{0}
     ```

- **Eliminar todos los stashes**: Si quieres limpiar todos los stashes guardados:
  ```bash
  git stash clear
  ```

## Ejercicios

1. Usar al menos una vez cada uno de los comandos vistos. Por cada uso, hacer los `diffs` necesarios para entender lo que cada comando hace exactamente.

## Recursos

- [Visualizing Git](https://git-school.github.io/visualizing-git/)
- [Explain Git with D3](https://onlywei.github.io/explain-git-with-d3/)
- [Git reset y revert (freecodecamp)](https://www.freecodecamp.org/espanol/news/la-guia-definitiva-para-git-reset-y-git-revert/)
