# 4. Técnicas de optimización de commits

- [Gestión de cambios antes de confirmar](#gestión-de-cambios-antes-de-confirmar)
- [Diferencias entre referencias](#diferencias-entre-referencias)
- [Trazabilidad del historial](#trazabilidad-del-historial)
- [Filtrado masivo de ficheros](#filtrado-masivo-de-ficheros)

## Gestión de cambios antes de confirmar

Antes de realizar un commit, Git permite seleccionar exactamente qué partes de los cambios incluir. Esto se hace con:

```bash
git add -p
```

Este comando presenta fragmentos de código (“hunks”) uno por uno y permite decidir si se añaden al staging o no. Es ideal para dividir cambios grandes en commits más pequeños y lógicos.

Opciones típicas durante la selección:

- `y` → añadir el hunk
- `n` → no añadirlo
- `s` → dividir el hunk en más pequeños
- `e` → editar manualmente el fragmento

También se puede editar el contenido staged con:

```bash
git reset -p
```

## Diferencias entre referencias

`git diff` permite comparar entre distintos puntos del historial:

- Cambios no preparados (working directory vs staging):

```bash
git diff
```

- Cambios preparados (staging vs último commit):

```bash
git diff --cached
```

- Comparar dos commits:

```bash
git diff HEAD~2 HEAD
```

## Trazabilidad del historial

Para investigar quién cambió una línea concreta:

```bash
git blame archivo.txt
```

Cada línea aparece junto con el SHA del commit, autor y fecha del cambio.

También puedes buscar cuándo apareció un término en el código:

```bash
git log -S"nombre_funcion"
```

Esto muestra commits donde la función fue añadida o eliminada.

## Filtrado masivo de ficheros

Git permite excluir archivos del control de versiones mediante el archivo `.gitignore`.

Ejemplo de `.gitignore` típico:

```
*.log
.env
node_modules/
dist/
```

También puedes aplicar filtros globales desde tu configuración:

```bash
git config --global core.excludesfile ~/.gitignore_global
```

Esto es útil para ignorar archivos personales o generados automáticamente que no deben compartirse.
