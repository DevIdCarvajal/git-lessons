# Ejercicios

## Ejercicio 1: Conectar con un remoto

1. Crea un nuevo repositorio local.
2. Añade un remoto falso con `git remote add`.
3. Lista los remotos con `git remote -v`.

## Ejercicio 2: Subir y bajar cambios

1. Crea un repositorio local con un commit.
2. Clónalo en otra carpeta.
3. Haz cambios en uno y súbelos con `git push`.
4. Sincroniza el otro con `git pull`.

## Ejercicio 3: Crear y usar un repositorio bare

1. Crea un repo bare con `git init --bare`.
2. Clónalo desde otra carpeta.
3. Realiza cambios y haz push al bare.
4. Clona desde otro equipo (o carpeta) y haz `pull`.

## Ejercicio 4: Resolver conflictos

1. Clona el mismo repo en dos carpetas.
2. Edita la misma línea de un archivo en ambos y haz commit.
3. Intenta hacer `push` desde ambos.
4. Resuelve el conflicto manualmente.
