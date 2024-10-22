# 2. Versionado y manejo de distintos escenarios de trabajo

- [Creación de alias de comandos](#creación-de-alias-de-comandos)
- [Etiquetado de versiones con `tags`](#etiquetado-de-versiones-con-tags)
- [Guardado temporal de cambios con `stash`](#guardado-temporal-de-cambios-con-stash)
- [Trabajando con ramas](#trabajando-con-ramas)
- [Ejercicios](#ejercicios)

## Creación de alias de comandos

En Git, es común trabajar con una gran variedad de comandos que, aunque poderosos, pueden resultar largos o repetitivos. Para optimizar el trabajo diario, Git permite crear **alias** para simplificar estos comandos.

- **¿Qué es un alias en Git?**: Un alias en Git es una forma abreviada de un comando o conjunto de comandos. Estos alias se configuran para que puedas ejecutar operaciones con menos teclas, mejorando tu productividad.

- **Cómo crear un alias**: Los alias se configuran utilizando el comando `git config`. Por ejemplo, si deseas acortar `git status` a simplemente `git st`, puedes ejecutar:
  ```bash
  git config --global alias.st status
  ```
  Después de configurar este alias, puedes usar `git st` en lugar de `git status`.

- **Alias recomendados**: Aquí algunos alias útiles que puedes configurar:
  ```bash
  git config --global alias.co checkout
  git config --global alias.br branch
  git config --global alias.cm commit
  git config --global alias.hist "log --oneline --graph --decorate --all"
  ```

- **Ver todos los alias configurados**: Para listar los alias que ya tienes configurados:
  ```bash
  git config --get-regexp alias
  ```

## Etiquetado de versiones con `tags`

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

## Guardado temporal de cambios con `stash`

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

## Trabajando con ramas

### Definición y consideraciones iniciales

Las **ramas** (*branches* en inglés) en Git son fundamentales para el trabajo en equipo y la gestión de características o arreglos de bugs en paralelo. Una rama permite a un desarrollador trabajar en una nueva característica sin interferir en el trabajo principal del proyecto.

- **¿Qué es una rama en Git?**: Una rama es simplemente un puntero a un commit específico en el historial. Git maneja ramas de manera muy eficiente, permitiendo cambiar rápidamente entre ellas.

- **¿Por qué usar ramas?**: Las ramas te permiten aislar tu trabajo. Esto es útil para trabajar en nuevas características, realizar pruebas o arreglar bugs sin interferir con el código de producción. Al finalizar el trabajo, las ramas se pueden fusionar con la rama principal (usualmente `main` o `master`).

- **Ramas locales y remotas**: Es importante recordar que una rama creada localmente no existirá en el servidor remoto hasta que la "empujes" (informalmente en español se suele usar el anglicismo *"pushees"*) explícitamente. Esto es útil si deseas trabajar en una característica sin que sea visible para el equipo hasta que esté lista.

### Operaciones básicas

1. **Crear una nueva rama**: Para crear una nueva rama llamada `feature1`:
   ```bash
   git branch feature1
   ```

2. **Cambiar de rama (`checkout`)**: Una vez creada la rama, puedes moverte a ella utilizando `checkout`:
   ```bash
   git checkout feature1
   ```

   Desde Git 2.23, también puedes usar el nuevo comando `git switch`:
   ```bash
   git switch feature1
   ```

3. **Crear y cambiar a una nueva rama en un solo paso**: Este comando te permite crear una nueva rama y cambiarte a ella directamente:
   ```bash
   git checkout -b feature1
   ```

4. **Fusionar ramas (`merge`)**: Una vez que termines de trabajar en una rama, puedes fusionar los cambios a la rama principal. Primero, asegúrate de estar en la rama de destino (por ejemplo, `main`):
   ```bash
   git checkout main
   ```
   Luego, puedes fusionar los cambios desde la rama `feature1`:
   ```bash
   git merge feature1
   ```
   Durante el proceso de fusión, puede que ocurran **conflictos** si las mismas líneas de código han sido modificadas en diferentes ramas. Git notificará al usuario sobre estos conflictos, y será necesario resolverlos manualmente antes de continuar con la fusión.

5. **Eliminar una rama**: Una vez fusionada, puedes eliminar la rama que ya no necesitas:
   ```bash
   git branch -d feature1
   ```

## Ejercicios

1. Crear dos alias:
 - Para hacer `commit`, que acepte un mensaje como parámetro.
 - Para crear una rama nueva y cambiarse a ella en un solo paso.
2. Etiquetado de dos versiones del proyecto, siendo una el primer `commit` y otra el tercero.
3. Crear una rama a partir de `main` llamada `first-revision` , modificar alguna de las tres entradas del cuaderno de bitácora y hacer `merge` de esos cambios a `main` .

## Recursos

- [Git Gud](https://nic-hartley.github.io/git-gud/)
- [Learn Git Branching](https://learngitbranching.js.org/?locale=es_ES)
