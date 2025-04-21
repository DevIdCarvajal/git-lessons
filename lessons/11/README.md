# 11. Submódulos e integración de proyectos

- [Submodules: creación y sincronización](#submodules-creación-y-sincronización)
- [Integración con herramientas externas](#integración-con-herramientas-externas)
- [Gestión de proyectos con dependencias compartidas](#gestión-de-proyectos-con-dependencias-compartidas)

## Submodules: creación y sincronización

Un submódulo permite incluir un repositorio Git dentro de otro. Se usa cuando un proyecto depende de otro que también tiene su propio control de versiones.

### Añadir un submódulo

```bash
git submodule add https://github.com/usuario/repo-libreria libs/repo-libreria
```

Esto actualiza dos archivos:

- `.gitmodules`: configuración del submódulo.
- `libs/repo-libreria`: carpeta que apunta al repo externo.

### Clonar un proyecto con submódulos

```bash
git clone --recursive url-del-repo
```

O bien después del clonado:

```bash
git submodule update --init --recursive
```

### Actualizar submódulos

```bash
git submodule update --remote
```

### Recorrer submódulos

```bash
git submodule foreach git pull
```

## Integración con herramientas externas

Los submódulos pueden ser gestionados por plataformas como:

- GitHub (como repos individuales vinculados).
- GitLab (con workflows para submódulos).
- Bitbucket (como dependencias enlazadas).

Se recomienda no usar submódulos para dependencias internas en evolución activa, ya que complica el flujo de trabajo.

## Gestión de proyectos con dependencias compartidas

Casos de uso comunes:

- Librerías compartidas entre varios proyectos.
- Código común reutilizable en distintos servicios.
- Separación entre frontend y backend.

Recomendaciones:

- Evitar cambios simultáneos en submódulo y proyecto padre.
- Hacer commits explícitos del cambio de versión del submódulo.
- Documentar los pasos necesarios para clonar y sincronizar correctamente.
