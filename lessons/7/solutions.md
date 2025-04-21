# Soluciones

## Ejercicio 1

```bash
mkdir proyecto
cd proyecto
git init
git remote add origin https://ejemplo.com/falso.git
git remote -v
```

## Ejercicio 2

```bash
mkdir repo-a && cd repo-a
git init
echo "hola" > archivo.txt
git add .
git commit -m "Inicio"
cd ..
git clone repo-a repo-b

# En repo-a
cd repo-a
echo "más cambios" >> archivo.txt
git commit -am "Cambios"
git push origin main

# En repo-b
cd ../repo-b
git pull origin main
```

## Ejercicio 3

```bash
mkdir central.git
cd central.git
git init --bare

# Clonar desde otra carpeta
cd ..
git clone central.git clon-a
cd clon-a
echo "hola" > hola.txt
git add .
git commit -m "Commit desde clon-a"
git push origin main
```

## Ejercicio 4

```bash
# En carpeta A
echo "línea A" > conflicto.txt
git commit -am "Cambio A"
git push origin main

# En carpeta B
echo "línea B" > conflicto.txt
git commit -am "Cambio B"
git pull origin main
# Resolver conflicto, luego:
git add conflicto.txt
git commit
```
