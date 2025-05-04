# Ejemplos de flujos de trabajo colaborativo en Git

## 1. Centralizado con una sola rama compartida (tipo SVN)

### Ramas

- En remoto:
  - `main`
- En local:
  - `main`

### Secuencia de acciones

1. Todos hacemos `clone` de remoto a local

2. Trabajamos en local:
    ```
    git add
    git commit -m "..."
    ```

3. Actualizamos cambios de remoto:
    ```
    git pull
    ```
    (Se resuelven conflictos si hay.)

4. Subimos cambios a remoto:
    ```
    git push
    ```

## 2. Centralizado con más de una rama en local

### Ramas

- En remoto:
  - `main`
- En local:
  - `main`
  - `feature`

### Secuencia de acciones

1. Todos hacemos `clone` de remoto a local

2. Trabajamos en nuestra rama local:
    ```
    git checkout -b feature
    git add
    git commit -m "..."
    ```

3. Actualizamos cambios de remoto en la rama compartida:
    ```
    git checkout main
    git pull
    ```
    (Se resuelven conflictos si hay.)

- Integramos nuestros cambios localmente:
  ```
  git merge feature
  ```
  (Se resuelven conflictos si hay.)

- Subimos cambios a remoto:
  ```
  git push
  ```

- Volvemos a nuestra rama e integramos la principal:
  ```
  git checkout feature
  git merge main
  ```

  O la borramos (preferentemente):
  ```
  git branch -d feature
  ```

## 3. GitFlow en local

### Ramas

- En remoto:
  - `main`
  - `develop`
  - `hotfix`
- En local:
  - `main`
  - `develop`
  - `hotfix`
  - `feature`

### Secuencia de acciones

- Las mismas que en el caso anterior, pero:
  - Primero se integran los cambios de nuestra rama en `develop`.
  - Cuando `develop` esté probado, se integran de `develop` a `main`.
- Se puede usar `hotfix` para arreglos urgentes, que se deben integrar en `develop` y `main`.

## 4. GitFlow en remoto

### Ramas

- En remoto:
  - `main`
  - `develop`
  - `hotfix`
  - `feature1`
  - `feature2`
  - ...
  - `featureN`
- En local:
  - `main`
  - `develop`
  - `hotfix`
  - `feature1`

### Secuencia de acciones

- Las mismas que en el caso anterior, salvo que:
  - Los cambios de nuestra rama (o `hotfix`) en `develop` no se hacen localmente, sino que se hace `push` de nuestra rama a remoto y se solicita la integración mediante `merge request` en la plataforma colaborativa, con la estrategia elegida (e.g., `merge` o `rebase`).
  - Del mismo modo, la integración de `develop` a `main` se hace via `merge request` en la plataforma colaborativa, con la estrategia elegida (e.g., `merge --squash`).
- Es decir, que solo se hace `push` de la rama propia y la integración se hace en remoto con `merge request`, aplicando en cada caso la estrategia que se prefiera.
