# Soluciones

## Ejercicio 1

```bash
echo "primero" > uno.txt
git add uno.txt
git commit -m "Commit inicial"
echo "segundo" > dos.txt
git add dos.txt
git commit --amend
```

## Ejercicio 2

```bash
echo "linea" >> prueba.txt
git commit -am "Commit 1"
echo "otra" >> prueba.txt
git commit -am "Commit 2"
git reset --soft HEAD~1
git status
```

## Ejercicio 3

```bash
nano algo.txt
git stash
git stash pop
```

## Ejercicio 4

```bash
echo "A" > a.txt && git commit -am "A"
echo "B" > b.txt && git commit -am "B"
echo "C" > c.txt && git commit -am "C"
git rebase -i HEAD~3  # cambiar pick a squash en los dos últimos
```

## Ejercicio 5

```bash
touch temp1.log temp2.tmp
git clean -n
git clean -f
```

## Ejercicio 6

```bash
git bisect start
git bisect bad
git bisect good abc123  # SHA de commit correcto
git bisect reset
```
