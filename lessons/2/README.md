# 2. Primeros pasos

- [Creación de repositorios](#creación-de-repositorios)
- [Configuración inicial](#configuración-inicial)
- [Anatomía de un repositorio](#anatomía-de-un-repositorio)
- [Creación de commits](#creación-de-commits)

## Creación de repositorios

Para crear un nuevo repositorio desde cero, usamos:

```bash
git init
```

Este comando inicializa un repositorio vacío en el directorio actual. Se crea un subdirectorio oculto llamado `.git`, donde Git almacena todo el historial y la configuración del proyecto.

Para clonar un repositorio existente:

```bash
git clone <url-del-repo>
```

Esto copia todos los archivos, historial y ramas remotas, dejando el repositorio listo para trabajar.

## Configuración inicial

Antes de hacer ningún commit, conviene establecer nuestra identidad en Git:

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@ejemplo.com"
```

Estas opciones se guardan en el archivo `~/.gitconfig`. Pueden redefinirse localmente en cada proyecto si se desea.

También es recomendable configurar el editor por defecto y el coloreado de salida:

```bash
git config --global core.editor "code --wait"
git config --global color.ui auto
```

## Anatomía de un repositorio

Un repositorio Git consta de tres áreas principales:

- **Working directory:** tu directorio de trabajo con los archivos del proyecto.
- **Staging area (índice):** zona temporal donde se preparan los cambios para confirmar.
- **Repositorio (HEAD):** historial oficial con todos los commits confirmados.

El flujo habitual es:

```
Edición → git add → Staging → git commit → Repositorio
```

Podemos visualizar el estado de estas zonas con:

```bash
git status
```

## Creación de commits

Un commit representa un punto en el tiempo del proyecto. Para crear uno, seguimos tres pasos:

1. Crear o modificar archivos.
2. Añadirlos al área de staging:
    ```bash
    git add archivo.txt
    ```
3. Confirmar los cambios:
    ```bash
    git commit -m "Mensaje claro y conciso"
    ```

Conviene escribir mensajes en modo imperativo, cortos pero descriptivos, y evitar ambigüedades como "cambios varios".

Podemos consultar el historial con:

```bash
git log --oneline
```

Y ver el detalle del último commit:

```bash
git show
```
