# Curso de Git, GitLab y GitHub

## 1. Introducción y primeros pasos

- Conceptos básicos del control de versiones
- Historia: Git vs. SVN (y otras alternativas)
- Definición y justificación de uso de Git
- Instalación y configuración básica
- Creación de un repositorio local
- Ciclo de vida de ficheros locales
  - Estados de los archivos ( `untracked`, `staged`, `committed` )
  - Comandos básicos ( `add`, `commit`, `status`, `log`, `diff` )

### Ejercicios

1. Instalar Git y crear un repositorio local para un proyecto llamado `moby-git` .
2. Versionar un cuaderno de bitácora que tenga tres entradas con diferentes contenidos de texto escritas en Markdown, cada una de ellas versionada con un `commit` diferente. En la segunda, además de texto, debe haber una imagen.
3. Comparar el contenido del primer y el tercer `commit` .

## 2. Versionado y manejo de distintos escenarios de trabajo

- Creación de alias de comandos
- Etiquetado de versiones con `tags` 
- Guardado temporal de cambios con `stash` 
- Trabajando con ramas
  - Definición y consideraciones iniciales
  - Operaciones básicas ( `branch`, `checkout`, `merge` )

### Ejercicios

1. Crear dos alias:
 - Para hacer `commit`, que acepte un mensaje como parámetro.
 - Para crear una rama nueva y cambiarse a ella en un solo paso.
2. Etiquetado de dos versiones del proyecto, siendo una el primer `commit` y otra el tercero.
3. Crear una rama a partir de `main` llamada `first-revision` , modificar alguna de las tres entradas del cuaderno de bitácora y hacer `merge` de esos cambios a `main` .

## 3. Herramientas gráficas y comandos avanzados

- Ejemplos de herramientas
  - Gitk
  - DiffMerge
  - SmartGit
  - GitKraken
  - SourceTree
- Cherry-picking y otros comandos avanzados
  - `cherry-pick`
  - `rev-parse`
  - `amend`
  - `clean`
  - `revert`
  - `rebase`

### Ejercicios

1. Instalar Gitk, DiffMerge, SmartGit, GitKraken y SourceTree y explorar las distintas herramientas para realizar y entender las operaciones básicas vistas hasta ahora: `commits`, `tags`, `diffs`, ramas, etc.
2. Hacer `cherry-picking` desde un `commit` de una rama a otro `commit` de otra rama.
3. Usar al menos una vez cada uno de los otros comandos avanzados vistos hasta ahora. Por cada uso, hacer los `diffs` necesarios para entender lo que cada comando hace exactamente.

## 4. Trabajo colaborativo

- Repositorios remotos
  - Protocolos de sincronización ( `https`, `ssh` )
  - Gestión de credenciales
  - Operativa básica ( `clone`, `fetch`, `push`, `pull` )
- GitLab vs. GitHub
    - Comparativa de plataformas
    - Flujos de trabajo
      - Forking Workflow
      - Centralized Workflow
      - GitFlow

### Ejercicios

#### En solitario

1. Clonar el repositorio de `progit` en español y generar el libro en PDF.
2. Crear un repositorio remoto con ficheros creados por la plataforma ( `README` y `LICENSE` ) en GitHub y clonarlo en local.
2. Añadir un fichero con algo de texto y sincronizarlo con el repositorio recién clonado.

#### Por parejas (trío en caso de impares)

Cada miembro de la pareja (o trío, en su caso) deberá:

1. Crear un repositorio remoto vacío en GitHub llamado  `moby-git` y sincronizarlo con el repo local homónimo.
2. Añadir al otro compañero como colaborador del repositorio y a continuación pedirle que lo clone, modifique algún fichero en la rama principal y sincronice de nuevo.
3. Sincronizar en local los cambios efectuados por el otro compañero:
    - En caso de haber conflictos, arreglarlos.
    - En otro caso, simular un escenario en el que sí los haya, acordándolo con el compañero (e.g., modificando ambos la misma línea después de hacer `push` el creador del repo y `pull` el/los colaboradores).
4. Sincronizar con remoto la resolución de los conflictos y pedirle al compañero que sincronice de nuevo, modifique algún fichero en una rama nueva y sincronice de nuevo.
5. Sincronizar los cambios del compañero y hacer `merge` de su rama creada con la principal en local. Resolver conflictos si los hubiese.
6. Repetir todos los ejercicios anteriores con GitLab.

#### Por equipos (de 3 o 4 personas)

```
[Pendiente]
- Forking Workflow
- Centralized Workflow
- GitFlow
```

# Recursos

[https://git-scm.com/]([https://git-scm.com/)  
[https://github.com/progit/progit2-es]([https://github.com/progit/progit2-es)

[https://training.github.com/downloads/es_ES/subversion-migration/]([https://training.github.com/downloads/es_ES/subversion-migration/)  
[https://rogerdudler.github.io/git-guide/index.es.html]([https://rogerdudler.github.io/git-guide/index.es.html)  
[https://learngitbranching.js.org/?locale=es_ES]([https://learngitbranching.js.org/?locale=es_ES)  
[https://onlywei.github.io/explain-git-with-d3/]([https://onlywei.github.io/explain-git-with-d3/)  
[https://git-school.github.io/visualizing-git/]([https://git-school.github.io/visualizing-git/)  
[https://nic-hartley.github.io/git-gud/]([https://nic-hartley.github.io/git-gud/)  
[https://githistory.xyz/]([https://githistory.xyz/)

[https://skills.github.com/]([https://skills.github.com/)  
[https://docs.github.com/es/get-started/getting-started-with-git]([https://docs.github.com/es/get-started/getting-started-with-git)
