# Soluciones

## Ejercicio 1

```bash
git checkout -b feature-x
echo "nueva funcionalidad" > f.txt
git add f.txt
git commit -m "Añade feature X"
git checkout main
git branch -d feature-x
```

## Ejercicio 2

```bash
git log --oneline
git checkout -b desde-antiguo abc1234
```

## Ejercicio 3

```bash
git tag v1.0
git tag -a v2.0 -m "Versión con mejoras"
git show v2.0
```

## Ejercicio 4

```bash
git push origin v1.0
git push origin v2.0
git push --tags
git ls-remote --tags origin
```

## Ejercicio 5

```bash
git format-patch -1 HEAD
# Copiar el archivo .patch a otra carpeta
cd ../nuevo-repo
git init
git apply ../repositorio-original/0001*.patch
```
