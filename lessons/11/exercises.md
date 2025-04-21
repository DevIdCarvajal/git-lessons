# Ejercicios

## Ejercicio 1: Añadir un submódulo

1. Crea dos repositorios Git: `main` y `lib`.
2. Desde `main`, añade `lib` como submódulo.
3. Haz commit del `.gitmodules`.

## Ejercicio 2: Clonar con submódulos

1. Clona el repo `main` en otra carpeta.
2. Ejecuta `git submodule update --init --recursive`.

## Ejercicio 3: Actualizar submódulo

1. Haz cambios en el submódulo `lib`.
2. Desde `main`, actualiza el puntero.
3. Haz commit del cambio en el submódulo.

## Ejercicio 4: Comandos útiles con submódulos

1. Usa `git submodule status`.
2. Usa `git submodule foreach` para ejecutar un comando.
