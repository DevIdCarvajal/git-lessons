# Soluciones

## Ejercicio 1

```bash
echo "uno" > a.txt && git commit -am "Uno"
echo "dos" > b.txt && git commit -am "Dos"
echo "tres" > c.txt && git commit -am "Tres"
git rebase -i HEAD~3  # Reordenar, cambiar mensaje, hacer squash
```

## Ejercicio 2

```bash
git checkout main
git cherry-pick abc123
```

## Ejercicio 3

```bash
git checkout -b nueva-rama
echo "Cambio" > nuevo.txt
git add .
git commit -m "Propuesta de cambio"
git push origin nueva-rama
# Luego se crea el PR desde GitHub/GitLab
```

## Ejercicio 4

(Se realiza desde la interfaz web de GitHub o GitLab)
1. Crear repo.
2. Entrar en Settings > Branches.
3. Añadir protección a `main`.
4. Crear una nueva rama y un PR desde esa rama.
