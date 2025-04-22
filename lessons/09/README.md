# 9. Visualización y herramientas gráficas

- [Uso de GitK, GitG y git log visual](#uso-de-gitk-gitg-y-git-log-visual)
- [Integración con entornos como IntelliJ y VSCode](#integración-con-entornos-como-intellij-y-vscode)

## Uso de GitK, GitG y git log visual

### git log con formato gráfico

```bash
git log --oneline --graph --all --decorate
```

Este comando permite ver las ramas y fusiones de forma gráfica en la terminal.

Puedes crear un alias para no escribirlo siempre:

```bash
git config --global alias.gra "log --oneline --graph --all --decorate"
```

### GitK

Herramienta visual incluida con Git. Muestra ramas, commits y permite explorar el historial de forma intuitiva.

```bash
gitk
```

### GitG

Otra alternativa visual muy completa para entornos Linux.

```bash
gitg
```

Ambas permiten:

- Ver el historial de forma visual.
- Comparar versiones de archivos.
- Navegar entre ramas y commits.

## Integración con entornos como IntelliJ y VSCode

### IntelliJ IDEA

Funciones integradas:

- Control de versiones desde el menú VCS.
- Vista gráfica del historial.
- Gestión de ramas y conflictos visualmente.
- Commit y push desde el entorno.

### Visual Studio Code (VSCode)

Extensión integrada de Git:

- Barra lateral para staging, commits y conflictos.
- Historial visual de commits.
- Compatibilidad con repositorios remotos.
- Integración con GitHub (Pull Requests, issues...).

Para mejorar la experiencia:

- Instalar extensión **Git Graph** para ver el historial visual.
- Usar atajos rápidos para operaciones comunes (`Ctrl + Shift + G`).
