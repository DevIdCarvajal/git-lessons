# Ejercicios

## Ejercicio 1: Crear y eliminar ramas

1. Crea una nueva rama llamada `feature-x`.
2. Añade un commit en esa rama.
3. Cambia a `main` y elimina `feature-x`.

## Ejercicio 2: Ramas desde referencia

1. Usa `git log` para encontrar un commit antiguo.
2. Crea una nueva rama desde ese commit.

## Ejercicio 3: Uso de etiquetas

1. Crea una etiqueta `v1.0` en el último commit.
2. Crea una etiqueta anotada `v2.0` con mensaje.
3. Usa `git show` para consultar su contenido.

## Ejercicio 4: Compartir etiquetas

1. Sube tus etiquetas a un repositorio remoto.
2. Verifica con `git ls-remote --tags origin`.

## Ejercicio 5: Crear y aplicar un parche

1. Haz un commit y genera un `.patch` con `git format-patch`.
2. Aplica ese parche en otro repositorio o carpeta limpia.
