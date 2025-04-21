# 10. Configuración avanzada de Git

- [Alias y personalización](#alias-y-personalización)
- [gitconfig y otras opciones útiles](#gitconfig-y-otras-opciones-útiles)
- [Uso de hooks (cliente y servidor)](#uso-de-hooks-cliente-y-servidor)

## Alias y personalización

Git permite definir alias para comandos frecuentes:

```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
```

Esto permite ejecutar, por ejemplo:

```bash
git co main
git st
```

## gitconfig y otras opciones útiles

Git guarda su configuración en tres niveles:

- Sistema (`/etc/gitconfig`)
- Usuario (`~/.gitconfig`)
- Repositorio (`.git/config`)

Algunas opciones recomendadas:

```bash
git config --global color.ui auto
git config --global core.editor "code --wait"
git config --global pull.rebase false
```

También puedes personalizar la firma de los commits o el comportamiento por defecto de `push`, `merge` o `log`.

Para ver toda la configuración actual:

```bash
git config --list
```

## Uso de hooks (cliente y servidor)

Los hooks son scripts que se ejecutan automáticamente en eventos clave del flujo de trabajo Git.

### Hooks del lado cliente

Se encuentran en `.git/hooks/` del repositorio. Ejemplos:

- `pre-commit`: ejecutado antes de confirmar.
- `commit-msg`: valida o modifica el mensaje.
- `post-commit`: tras realizar un commit.
- `pre-push`: antes de subir cambios.

### Hooks del lado servidor

En repositorios bare. Ejemplos:

- `pre-receive`: antes de aceptar un push.
- `update`: durante el push, por cada rama.
- `post-receive`: después de aceptar los cambios.

Los hooks son scripts de shell (bash, Python...) que deben ser ejecutables.

### Ejemplo: pre-commit para validar formato

```bash
#!/bin/bash
black --check .
if [ $? -ne 0 ]; then
  echo "⚠️ Formato incorrecto. Ejecuta black antes de hacer commit."
  exit 1
fi
```

Hazlo ejecutable con:

```bash
chmod +x .git/hooks/pre-commit
```
