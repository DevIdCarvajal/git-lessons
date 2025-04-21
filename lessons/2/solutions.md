# Soluciones

## Ejercicio 1: Crear un nuevo repositorio

```bash
mkdir mi-proyecto-git
cd mi-proyecto-git
git init
echo "# Mi proyecto Git" > README.md
git add README.md
git commit -m "Primer commit con README"
```

## Ejercicio 2: Configuración inicial

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@ejemplo.com"
git config --list
```

## Ejercicio 3: Anatomía del repositorio

```bash
touch archivo1.txt archivo2.txt
git status
git add archivo1.txt
git status
git commit -m "Añade archivo1"
```

## Ejercicio 4: Consulta del historial

```bash
echo "Nueva línea" >> archivo2.txt
git add archivo2.txt
git commit -m "Actualiza archivo2"
git log
git show
```
