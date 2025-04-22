# Ejercicios

## Ejercicio 1: Añadir por partes

1. Modifica varias secciones de un mismo archivo.
2. Usa `git add -p` y selecciona solo una parte.
3. Realiza un commit con un mensaje adecuado.

## Ejercicio 2: Comparar diferencias

1. Crea tres versiones distintas de un archivo (con commits).
2. Usa `git diff HEAD~2 HEAD` para ver los cambios.
3. Explora también `git diff` y `git diff --cached`.

## Ejercicio 3: Rastrear líneas

1. Elige un archivo con varias versiones.
2. Ejecuta `git blame` sobre él.
3. Usa `git log -S"palabra_clave"` para buscar un término concreto.

## Ejercicio 4: Crear y aplicar .gitignore

1. Crea archivos temporales como `debug.log`, `build/`, `.env`.
2. Crea un archivo `.gitignore` que los excluya.
3. Comprueba que `git status` ya no los detecta.
