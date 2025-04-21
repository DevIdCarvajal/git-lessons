# 12. Buenas prácticas

- [Atomicidad y frecuencia de commits](#atomicidad-y-frecuencia-de-commits)
- [Validaciones antes del commit](#validaciones-antes-del-commit)
- [Redacción de mensajes de commit](#redacción-de-mensajes-de-commit)
- [Uso de ramas y estrategias de branching](#uso-de-ramas-y-estrategias-de-branching)
- [Workflows: opciones habituales y recomendaciones](#workflows-opciones-habituales-y-recomendaciones)

## Atomicidad y frecuencia de commits

Un commit debe representar un cambio **coherente y completo**: una funcionalidad, una corrección, una refactorización.

Recomendaciones:

- Commits pequeños y específicos.
- Evitar mezclar tareas en un solo commit.
- Cometer frecuentemente para facilitar el rollback si es necesario.

## Validaciones antes del commit

Automatizar la validación del código antes de hacer commit ayuda a mantener la calidad.

Opciones comunes:

- Linters y formateadores (`eslint`, `black`, `prettier`...).
- Tests automáticos (`pytest`, `jest`...).
- Hooks de Git (`pre-commit`, `commit-msg`...).

Ejemplo con pre-commit:

```bash
npx eslint .
[ $? -ne 0 ] && exit 1
```

## Redacción de mensajes de commit

Un buen mensaje de commit debe:

- Explicar **qué** se hizo y **por qué**.
- Usar modo imperativo: "Corrige bug", "Añade validación", "Refactoriza..."

Formato sugerido:

```
Tipo: descripción breve

[Opcional] Detalles adicionales o referencias a issues.
```

Ejemplo:

```
Fix: corrige error en login

El token de autenticación no se regeneraba correctamente.
```

## Uso de ramas y estrategias de branching

Recomendaciones:

- Usar nombres claros y consistentes: `feature/`, `bugfix/`, `hotfix/`, `release/`.
- Eliminar ramas cuando se fusionan.
- Mantener `main` siempre funcional.

## Workflows: opciones habituales y recomendaciones

### GitHub Flow

- Rama por feature.
- PR contra `main`.
- Merge tras revisión y tests.

### Git Flow

- Ramas `main`, `develop`, `feature/`, `release/`, `hotfix/`.
- Flujo más estructurado y predecible.

### Trunk Based Development

- Trabajo directo sobre `main`.
- Uso de feature flags.
- Validación continua automática.

Escoger un flujo adecuado depende del tamaño del equipo, frecuencia de releases y complejidad del producto.
