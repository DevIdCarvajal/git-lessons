# Ejercicios

## Ejercicio 1: Modificar un commit anterior

1. Crea y confirma un archivo.
2. Añade otro archivo olvidado.
3. Usa `git commit --amend` para incluirlo en el mismo commit.

## Ejercicio 2: Reset de cambios

1. Haz varios commits.
2. Ejecuta `git reset --soft HEAD~1`.
3. Comprueba el estado con `git status`.

## Ejercicio 3: Guardar y recuperar trabajo temporal

1. Edita varios archivos sin confirmar.
2. Usa `git stash` para guardarlos.
3. Usa `git stash pop` para recuperarlos.

## Ejercicio 4: Rebase interactivo

1. Haz tres commits simples.
2. Ejecuta `git rebase -i HEAD~3`.
3. Fusiona los dos últimos con `squash`.

## Ejercicio 5: Limpiar archivos no versionados

1. Crea archivos sueltos (sin añadir a Git).
2. Usa `git clean -n` y `git clean -f` para eliminarlos.

## Ejercicio 6: Detectar commit problemático

1. Crea un repositorio de prueba con varios commits.
2. Introdúcelo a propósito un bug en uno.
3. Usa `git bisect` para encontrar el commit que lo introdujo.
