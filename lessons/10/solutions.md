# Soluciones

## Ejercicio 1

```bash
git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.lg "log --oneline --graph"
git co -b nueva-rama
git ci -am "Cambios"
git lg
```

## Ejercicio 2

```bash
git config --list
git config --global core.editor "nano"
git config --global color.ui auto
```

## Ejercicio 3

```bash
cat > .git/hooks/pre-commit << 'EOF'
#!/bin/bash
if [ -f *.tmp ]; then
  echo "No se permiten archivos .tmp"
  exit 1
fi
EOF
chmod +x .git/hooks/pre-commit
```

## Ejercicio 4

```bash
cd repo-central.git/hooks
cat > post-receive << 'EOF'
#!/bin/bash
echo "Push recibido en $(date)" >> ../push.log
EOF
chmod +x post-receive
```
