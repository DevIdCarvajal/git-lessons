# 3. Referencias, revisiones y rutas

- [Comandos habituales](#comandos-habituales)
- [Referencias útiles](#referencias-útiles)
- [Nomenclatura de etiquetas y ramas](#nomenclatura-de-etiquetas-y-ramas)
- [Referencias por mensaje de commit](#referencias-por-mensaje-de-commit)
- [Herramienta rev-parse](#herramienta-rev-parse)

## Comandos habituales

Muchos comandos en Git permiten operar sobre revisiones concretas y rutas de archivos al mismo tiempo. Por ejemplo:

```bash
git show HEAD~1 -- src/index.js
```

Esto muestra el estado del archivo `src/index.js` en el commit anterior al actual (`HEAD~1`).

Otros comandos similares:

- `git log ruta/archivo`: historial limitado a un archivo.
- `git diff commit1 commit2 -- archivo`: diferencias de un archivo entre dos commits.
- `git checkout commit -- archivo`: recuperar un archivo tal como estaba en otro commit.

## Referencias útiles

Git permite referenciar commits de muchas formas distintas:

| Referencia | Significado |
|------------|-------------|
| `HEAD` | Último commit confirmado en la rama actual. |
| `HEAD~1` o `HEAD^` | Un commit antes que el actual. |
| `HEAD~2` | Dos commits antes. |
| `nombre-rama` | El último commit de una rama. |
| `nombre-tag` | Commit asociado a una etiqueta. |
| `SHA1` | Identificador único de un commit. |

Las referencias pueden combinarse entre sí:

```bash
git diff HEAD~1 HEAD
git checkout nombre-rama~2
```

También se puede abreviar un SHA1 siempre que no haya ambigüedad:

```bash
git checkout 3a5f2c
```

## Nomenclatura de etiquetas y ramas

Internamente, Git organiza las referencias bajo distintos prefijos:

- `refs/heads/`: ramas locales
- `refs/remotes/`: ramas remotas
- `refs/tags/`: etiquetas

Puedes ver todas las referencias con:

```bash
git show-ref
```

Y las ramas con:

```bash
git branch -a
```

## Referencias por mensaje de commit

Git permite buscar commits por contenido textual de su mensaje:

```bash
git log -S"nombre_funcion"
```

También se puede usar:

```bash
git show :/fix
```

El operador `:/texto` busca hacia atrás en el historial hasta encontrar el primer commit cuyo mensaje contenga esa cadena. Muy útil para localizar cambios antiguos.

## Herramienta rev-parse

El comando `git rev-parse` es una herramienta interna muy útil para inspeccionar y validar referencias:

```bash
git rev-parse HEAD
```

Devuelve el SHA1 completo del commit actual. También permite componer rutas y referencias de forma avanzada.

Para aprender más:

```bash
man gitrevisions
```

O consultar: [https://git-scm.com/docs/gitrevisions](https://git-scm.com/docs/gitrevisions)
