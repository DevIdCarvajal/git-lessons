# 4. Ramas en Git

- [Concepto y beneficios del uso de ramas](#concepto-y-beneficios-del-uso-de-ramas)
- [Crear, listar y cambiar entre ramas](#crear-listar-y-cambiar-entre-ramas)
- [Fusión de ramas y resolución de conflictos](#fusión-de-ramas-y-resolución-de-conflictos)
- [Ejercicios](#ejercicios)

## Concepto y beneficios del uso de ramas

Las **ramas** (*branches* en inglés) en Git son fundamentales para el trabajo en equipo y la gestión de características o arreglos de bugs en paralelo. Una rama permite a un desarrollador trabajar en una nueva característica sin interferir en el trabajo principal del proyecto.

- **¿Qué es una rama en Git?**: Una rama es simplemente un puntero a un commit específico en el historial. Git maneja ramas de manera muy eficiente, permitiendo cambiar rápidamente entre ellas.

- **¿Por qué usar ramas?**: Las ramas te permiten aislar tu trabajo. Esto es útil para trabajar en nuevas características, realizar pruebas o arreglar bugs sin interferir con el código de producción. Al finalizar el trabajo, las ramas se pueden fusionar con la rama principal (usualmente `main` o `master`).

- **Ramas locales y remotas**: Es importante recordar que una rama creada localmente no existirá en el servidor remoto hasta que la "empujes" (informalmente en español se suele usar el anglicismo *"pushees"*) explícitamente. Esto es útil si deseas trabajar en una característica sin que sea visible para el equipo hasta que esté lista.

## Crear, listar y cambiar entre ramas

1. **Crear una nueva rama**: Para crear una nueva rama llamada `feature1`:
   ```bash
   git branch feature1
   ```

2. **Cambiar de rama (`checkout`)**: Una vez creada la rama, puedes moverte a ella utilizando `checkout`:
   ```bash
   git checkout feature1
   ```

   Desde Git 2.23, también puedes usar el nuevo comando `git switch`:
   ```bash
   git switch feature1
   ```

3. **Crear y cambiar a una nueva rama en un solo paso**: Este comando te permite crear una nueva rama y cambiarte a ella directamente:
   ```bash
   git checkout -b feature1
   ```

4. **Eliminar una rama**: Una vez fusionada, puedes eliminar la rama que ya no necesitas:
   ```bash
   git branch -d feature1
   ```

## Fusión de ramas y resolución de conflictos

Una vez que termines de trabajar en una rama, puedes fusionar (`merge`) los cambios a la rama principal. Primero, asegúrate de estar en la rama de destino (por ejemplo, `main`):
   ```bash
   git checkout main
   ```
   Luego, puedes fusionar los cambios desde la rama `feature1`:
   ```bash
   git merge feature1
   ```
   Durante el proceso de fusión, puede que ocurran **conflictos** si las mismas líneas de código han sido modificadas en diferentes ramas. Git notificará al usuario sobre estos conflictos, y será necesario resolverlos manualmente antes de continuar con la fusión.

## Ejercicios

1. Crear una rama a partir de `main` llamada `first-revision` , modificar alguna de las tres entradas del cuaderno de bitácora y hacer `merge` de esos cambios a `main` .
2. Crear otra rama a partir de `first-revision` llamada `second-revision` , modificar la misma entrada del ejercicio anterior, en la misma línea, hacer `merge` a `main` y resolver el conflicto.

## Recursos

- [Git Gud](https://nic-hartley.github.io/git-gud/)
- [Learn Git Branching](https://learngitbranching.js.org/?locale=es_ES)
