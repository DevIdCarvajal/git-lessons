# Soluciones

## Ejercicio 1

```bash
echo "Primera versión" > ejemplo.txt
git add ejemplo.txt
git commit -m "Primera versión del archivo"

echo "Segunda línea" >> ejemplo.txt
git commit -am "Añade segunda línea"

git show HEAD~1 -- ejemplo.txt
```

## Ejercicio 2

```bash
echo "Cambio 1" >> ejemplo.txt
git commit -am "Cambio 1"
echo "Cambio 2" >> ejemplo.txt
git commit -am "Cambio 2"
echo "Cambio 3" >> ejemplo.txt
git commit -am "Cambio 3"

git diff HEAD~2 HEAD~1 -- ejemplo.txt
```

## Ejercicio 3

```bash
git commit --allow-empty -m "Corrige error en login"
git show :/login
```

## Ejercicio 4

```bash
git checkout -b nueva-rama
echo "Desde rama nueva" > rama.txt
git add rama.txt
git commit -m "Commit en nueva rama"
git tag v1.0
git show-ref
```

## Ejercicio 5

```bash
git log --oneline
git checkout <sha-abreviado>
git checkout main
```
