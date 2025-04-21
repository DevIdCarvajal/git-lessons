# Soluciones

## Ejercicio 1

```bash
mkdir main lib
cd lib
git init
echo "librería" > lib.txt
git add . && git commit -m "Inicio lib"

cd ../main
git init
git submodule add ../lib libs/lib
git commit -am "Añade submódulo lib"
```

## Ejercicio 2

```bash
git clone --recursive ../main clon-main
# o:
git clone ../main clon-main
cd clon-main
git submodule update --init --recursive
```

## Ejercicio 3

```bash
cd libs/lib
echo "cambio" >> lib.txt
git commit -am "Update"
cd ../..
git add libs/lib
git commit -m "Actualiza puntero de submódulo"
```

## Ejercicio 4

```bash
git submodule status
git submodule foreach git pull
```
