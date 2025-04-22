# 7. Repositorios remotos y colaboración

- [Gestión de remotos](#gestión-de-remotos)
- [Push, pull y sincronización](#push-pull-y-sincronización)
- [Repositorios bare](#repositorios-bare)
- [Resolución de conflictos](#resolución-de-conflictos)

## Gestión de remotos

Los remotos permiten conectar tu repositorio local con uno alojado en plataformas como GitHub, GitLab o Bitbucket.

### Ver remotos configurados

```bash
git remote -v
```

### Añadir un nuevo remoto

```bash
git remote add origin https://github.com/usuario/repo.git
```

### Cambiar la URL de un remoto

```bash
git remote set-url origin nueva-url
```

### Eliminar un remoto

```bash
git remote remove origin
```

## Push, pull y sincronización

### Subir cambios al repositorio remoto

```bash
git push origin main
```

### Traer cambios del remoto

```bash
git pull origin main
```

También puedes separar el fetch del merge:

```bash
git fetch origin
git merge origin/main
```

### Clonar un repositorio remoto

```bash
git clone https://github.com/usuario/repo.git
```

## Repositorios bare

Un repositorio "bare" es un repositorio sin working directory. Se utiliza como repositorio central compartido:

```bash
git init --bare nombre.git
```

Se puede clonar desde él o hacer push/pull como si fuera un servidor.

## Resolución de conflictos

Cuando dos ramas modifican la misma parte de un archivo, Git no puede resolver el conflicto automáticamente.

1. Edita los archivos con conflictos y elimina las marcas:

```plaintext
<<<<<<< HEAD
Tu cambio
=======
Cambio remoto
>>>>>>> origin/main
```

2. Añade los archivos resueltos:

```bash
git add archivo
```

3. Finaliza el merge:

```bash
git commit
```

También puedes usar herramientas gráficas como `git mergetool` o los asistentes de VSCode.
