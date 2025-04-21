# Ejercicios

## Ejercicio 1: Crear alias

1. Crea alias para `checkout`, `commit` y `log`.
2. Comprueba que funcionan correctamente.

## Ejercicio 2: Revisar y modificar configuración

1. Ejecuta `git config --list`.
2. Cambia el editor por defecto.
3. Añade alguna configuración extra como el coloreado.

## Ejercicio 3: Hook de pre-commit

1. Crea un archivo `.git/hooks/pre-commit`.
2. Añade un script que bloquee el commit si existe un archivo `.tmp`.
3. Hazlo ejecutable y pruébalo.

## Ejercicio 4: Hook de post-receive (servidor)

1. En un repo `--bare`, crea el hook `post-receive`.
2. Añade un mensaje de log para cada push.
3. Pruébalo desde un repo clonado.
