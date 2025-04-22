# Soluciones

## Ejercicio 1

```bash
nano app.js  # editar varias partes
git add -p
git commit -m "Corrige función A sin tocar función B"
```

## Ejercicio 2

```bash
echo "Versión 1" > archivo.txt
git commit -am "Versión 1"
echo "Versión 2" >> archivo.txt
git commit -am "Versión 2"
echo "Versión 3" >> archivo.txt
git commit -am "Versión 3"

git diff HEAD~2 HEAD
git diff
git diff --cached
```

## Ejercicio 3

```bash
git blame archivo.txt
git log -S"palabra_clave"
```

## Ejercicio 4

```bash
echo "debug.log" > .gitignore
echo ".env" >> .gitignore
echo "build/" >> .gitignore

touch debug.log .env
mkdir build
git status  # no deberían aparecer
```
