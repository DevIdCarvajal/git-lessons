# 5. Rescribir el historial

- [Uso de amend, reset, revert, stash y rebase](#uso-de-amend-reset-revert-stash-y-rebase)
- [Limpieza del repositorio](#limpieza-del-repositorio)
- [Análisis de errores con bisect](#análisis-de-errores-con-bisect)

## Uso de amend, reset, revert, stash y rebase

### git commit --amend

Permite modificar el último commit, ya sea su mensaje o su contenido:

```bash
git commit --amend
```

Si has olvidado añadir un archivo:

```bash
git add archivo
git commit --amend
```

### git reset

Mueve el puntero `HEAD` a otro commit, modificando también staging y/o working directory:

- Soft: mueve HEAD, mantiene staging:
  ```bash
  git reset --soft HEAD~1
  ```

- Mixed (por defecto): limpia staging:
  ```bash
  git reset HEAD~1
  ```

- Hard: borra todo lo posterior:
  ```bash
  git reset --hard HEAD~1
  ```

### git revert

Deshace un commit generando uno nuevo inverso:

```bash
git revert abc123
```

Seguro para ramas compartidas.

### git stash

Guarda temporalmente cambios sin confirmar:

```bash
git stash
```

Y los recupera con:

```bash
git stash pop
```

### git rebase

Permite reorganizar commits:

```bash
git rebase -i HEAD~3
```

Usos habituales:

- Cambiar mensajes (`reword`)
- Fusionar commits (`squash`)
- Editar contenido (`edit`)

## Limpieza del repositorio

Git puede eliminar archivos no versionados con:

```bash
git clean -n  # Vista previa
git clean -f  # Elimina archivos
```

Usar `-d` para directorios, `-x` para ignorados.

## Análisis de errores con bisect

`git bisect` ayuda a encontrar qué commit introdujo un fallo:

```bash
git bisect start
git bisect bad
git bisect good <commit-bueno>
```

Git elegirá commits intermedios para probar. Marca cada uno como `good` o `bad` hasta hallar el culpable.

Finalizar:

```bash
git bisect reset
```
