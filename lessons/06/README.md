# 6. Trabajo en paralelo

- [Ramas: creación, eliminación y cambio de base](#ramas-creación-eliminación-y-cambio-de-base)
- [Etiquetas: creación, uso y publicación](#etiquetas-creación-uso-y-publicación)
- [Creación y aplicación de parches](#creación-y-aplicación-de-parches)

## Ramas: creación, eliminación y cambio de base

Las ramas permiten desarrollar funcionalidades en paralelo sin afectar la rama principal.

### Crear una nueva rama

```bash
git branch mi-rama
```

O directamente cambiar a ella:

```bash
git checkout -b mi-rama
```

### Cambiar entre ramas

```bash
git checkout main
```

### Eliminar una rama

```bash
git branch -d mi-rama
```

### Crear una rama desde otro commit

```bash
git checkout -b nueva-rama HEAD~2
```

También puedes hacer:

```bash
git checkout -b hotfix v1.0
```

## Etiquetas: creación, uso y publicación

Las etiquetas (`tags`) se utilizan para marcar puntos importantes del historial, como versiones de producción.

### Crear una etiqueta ligera

```bash
git tag v1.0
```

### Crear una etiqueta anotada

```bash
git tag -a v1.0 -m "Versión estable 1.0"
```

### Ver etiquetas

```bash
git tag
```

### Mostrar detalles de una etiqueta

```bash
git show v1.0
```

### Subir etiquetas a remoto

```bash
git push origin v1.0
```

Para subir todas:

```bash
git push --tags
```

## Creación y aplicación de parches

Puedes generar un archivo `.patch` a partir de commits y compartirlo.

### Crear parche del último commit

```bash
git format-patch -1 HEAD
```

Esto genera un archivo `.patch` con el contenido del commit.

### Aplicar un parche

```bash
git apply archivo.patch
```

Este sistema se utiliza en entornos donde no se puede hacer push directo, o para revisar cambios antes de integrarlos.
