# 8. Flujos de trabajo colaborativos

- [Merge vs rebase vs cherrypick](#merge-vs-rebase-vs-cherrypick)
- [Pull Requests y Merge Requests](#pull-requests-y-merge-requests)
- [Integración en plataformas colaborativas](#integración-en-plataformas-colaborativas)

## Merge vs rebase vs cherrypick

| Técnica       | Descripción |
|---------------|-------------|
| `merge`       | Combina ramas creando un nuevo commit de fusión. |
| `rebase`      | Reescribe commits para aplicar en otra base. Muy útil para limpieza de historial. |
| `cherry-pick` | Copia un commit concreto a otra rama sin fusionar ramas completas. |

### Ejemplo de rebase interactivo

```bash
git rebase -i HEAD~3
```

### Cherry-pick de un commit específico

```bash
git cherry-pick abc123
```

## Pull Requests y Merge Requests

Los PR (GitHub) o MR (GitLab) permiten proponer cambios, revisarlos y discutirlos antes de fusionarlos.

Ventajas:
- Fomentan la revisión de código.
- Permiten automatizar pruebas antes de hacer merge.
- Documentan los motivos detrás de cada cambio.

Pasos típicos:
1. Crear una rama con los cambios.
2. Subirla al repositorio remoto.
3. Crear el PR/MR desde la plataforma.
4. Asignar revisores y discutir.
5. Aprobar y hacer merge.

## Integración en plataformas colaborativas

Git se integra con servicios como:

- **GitHub**: Repositorios públicos y privados, GitHub Actions, PRs.
- **GitLab**: CI/CD potente, Merge Requests, gestión de proyectos.
- **Bitbucket**: Integración con Jira, pipelines.

Estos servicios permiten:

- Gestionar ramas y revisiones.
- Automatizar pruebas y despliegues.
- Configurar protecciones sobre ramas importantes.
