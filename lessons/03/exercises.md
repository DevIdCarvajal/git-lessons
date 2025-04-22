# Ejercicios

## Ejercicio 1: Mostrar versiones anteriores

1. Añade varias líneas a un archivo existente y haz commit.
2. Vuelve a modificarlo y haz otro commit.
3. Usa `git show HEAD~1 -- archivo` para ver cómo era antes.

## Ejercicio 2: Comparar revisiones

1. Haz tres commits con cambios distintos en el mismo archivo.
2. Usa `git diff HEAD~2 HEAD~1 -- archivo` para comparar versiones.

## Ejercicio 3: Buscar por mensaje de commit

1. Haz un commit cuyo mensaje contenga la palabra `login`.
2. Usa `git show :/login` para localizarlo.

## Ejercicio 4: Explorar ramas y etiquetas

1. Crea una nueva rama y haz un commit.
2. Crea una etiqueta (`tag`) en ese commit.
3. Usa `git show-ref` para listar todas las referencias.

## Ejercicio 5: Revisar SHA y abreviaciones

1. Usa `git log` para obtener el SHA de un commit.
2. Usa `git checkout <sha-corto>` para cambiar a ese commit.
3. Vuelve a `main` con `git checkout main`.
