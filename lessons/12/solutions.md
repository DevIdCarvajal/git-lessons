# Soluciones

## Ejercicio 1

```bash
git add -p
# Seleccionar cambios por partes
git commit -m "Añade validación en formulario"
git add -p
git commit -m "Corrige navegación en menú"
```

## Ejercicio 2

```bash
echo '#!/bin/bash' > .git/hooks/pre-commit
echo 'if ls *.tmp 1> /dev/null 2>&1; then echo "Bloqueado por .tmp"; exit 1; fi' >> .git/hooks/pre-commit
chmod +x .git/hooks/pre-commit
```

## Ejercicio 3

```bash
git commit --amend -m "Refactor: separa lógica de login"
```

## Ejercicio 4

Propuesta de convención:

- `feature/nombre-funcionalidad`
- `bugfix/id-incidencia`
- `hotfix/nombre-urgente`

Flujo recomendado: **GitHub Flow** por su sencillez y buena integración con PRs y automatizaciones.
