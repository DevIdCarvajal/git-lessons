# 4. Trabajo colaborativo

- [Repositorios remotos](#repositorios-remotos)
- [GitLab vs. GitHub](#gitlab-vs-github)
- [Ejercicios](#ejercicios)

## Repositorios remotos

Uno de los aspectos más poderosos de Git es su capacidad para trabajar de forma distribuida, permitiendo a múltiples personas colaborar en proyectos desde diferentes ubicaciones. Esto se logra mediante la sincronización de repositorios remotos. Un repositorio remoto es una copia del proyecto almacenada en un servidor que permite a los usuarios compartir cambios y colaborar de manera eficiente.

### 1. Protocolos de sincronización

Git permite conectar repositorios locales con remotos mediante distintos protocolos. Los más comunes son:

#### a. HTTPS

- **Descripción**: Es el protocolo más sencillo de configurar, ya que solo requiere una URL y permite la autenticación a través de usuario y contraseña o token.
- **Ventajas**:
  - Fácil de usar y configurar.
  - No requiere configuraciones adicionales en el cliente.
  - Soporte en prácticamente cualquier plataforma.
- **Desventajas**:
  - Requiere autenticación cada vez que se hace `push` o `pull` (aunque se puede evitar guardando las credenciales).
  - Puede ser más lento que otros protocolos en operaciones intensivas.
  
- **Ejemplo**:
  ```bash
  git clone https://github.com/usuario/repositorio.git
  ```

#### b. SSH

- **Descripción**: El protocolo SSH es más rápido y seguro, ya que utiliza claves SSH para la autenticación en lugar de contraseñas.
- **Ventajas**:
  - Mayor seguridad debido a la autenticación mediante claves.
  - No requiere ingresar la contraseña cada vez.
  - Generalmente más rápido que HTTPS.
  
- **Desventajas**:
  - Requiere configuración previa de las claves SSH tanto en el cliente como en el servidor.
  
- **Ejemplo**:
  ```bash
  git clone git@github.com:usuario/repositorio.git
  ```

### 2. Gestión de credenciales

Al trabajar con repositorios remotos, es necesario autenticarte para poder realizar operaciones como `push` y `pull`. Git ofrece diferentes maneras de gestionar las credenciales:

#### a. Almacenamiento de credenciales en caché

Puedes configurar Git para que almacene temporalmente tus credenciales en caché, evitando tener que introducirlas cada vez:
```bash
git config --global credential.helper cache
```
Esto mantendrá las credenciales en caché durante un tiempo determinado.

#### b. Almacenamiento permanente

Para evitar ingresar las credenciales en cada operación, puedes almacenarlas permanentemente (solo recomendado en sistemas seguros):
```bash
git config --global credential.helper store
```

#### c. Autenticación mediante SSH

SSH es otra manera de autenticarte sin necesidad de ingresar una contraseña cada vez, siempre y cuando hayas configurado correctamente tus claves SSH en Git y en las plataformas remotas.

### 3. Operativa básica

Al trabajar con repositorios remotos, los comandos más básicos son `clone`, `fetch`, `push` y `pull`. Estos comandos permiten sincronizar los cambios entre los repositorios locales y remotos.

#### a. `clone`

El comando `git clone` crea una copia de un repositorio remoto en tu máquina local.

- **Uso**:
  ```bash
  git clone <url-del-repositorio>
  ```

- **Ejemplo**:
  ```bash
  git clone https://github.com/usuario/proyecto.git
  ```

#### b. `fetch`

`git fetch` descarga todos los cambios del repositorio remoto sin modificar el historial o el estado del directorio de trabajo local. Es útil para obtener actualizaciones sin integrarlas automáticamente.

- **Uso**:
  ```bash
  git fetch origin
  ```

#### c. `push`

`git push` permite enviar los commits locales al repositorio remoto. Esto publica tus cambios para que otros colaboradores puedan acceder a ellos.

- **Uso**:
  ```bash
  git push origin <nombre-de-la-rama>
  ```

#### d. `pull`

`git pull` es una combinación de `fetch` y `merge`. Descarga los cambios del repositorio remoto y los fusiona automáticamente con tu rama actual.

- **Uso**:
  ```bash
  git pull origin <nombre-de-la-rama>
  ```

## GitLab vs. GitHub

GitLab y GitHub son dos de las plataformas más populares para alojar repositorios Git y colaborar en proyectos. Aunque ambas comparten muchas características, cada una tiene algunas particularidades que pueden hacerla más adecuada para ciertos contextos.

### 1. Comparativa de plataformas

#### GitLab

- **Descripción**: GitLab es una plataforma completa para DevOps, que incluye no solo alojamiento de repositorios Git, sino también herramientas de CI/CD, gestión de proyectos y pipelines automatizados.
- **Ventajas**:
  - Pipeline de CI/CD integrado de manera nativa.
  - Mejor enfoque en la gestión de proyectos privados.
  - Ofrece una versión autoalojada para empresas que prefieren gestionar sus propios servidores.
- **Desventajas**:
  - Menor comunidad en comparación con GitHub, especialmente en el ámbito de proyectos públicos.
  - La versión gratuita es menos atractiva en términos de características avanzadas.

#### GitHub

- **Descripción**: GitHub es la plataforma de Git más conocida, especialmente por su integración con la comunidad de código abierto. Fue adquirida por Microsoft en 2018.
- **Ventajas**:
  - Gran comunidad de desarrolladores y proyectos.
  - Integración fluida con herramientas de CI/CD como GitHub Actions.
  - Interfaces muy intuitivas.
- **Desventajas**:
  - Algunas funcionalidades avanzadas requieren un plan de pago.
  - Históricamente se ha centrado más en el uso para repositorios públicos, aunque esto ha cambiado.

### 2. Flujos de trabajo

Los flujos de trabajo en Git son patrones establecidos que los equipos siguen para colaborar de manera eficiente. Dependiendo del tamaño del equipo y de las necesidades del proyecto, se pueden utilizar diferentes flujos de trabajo.

#### a. Forking Workflow

El flujo de trabajo de forking es común en proyectos de código abierto. Cada colaborador realiza un "fork" (una copia del repositorio) y trabaja en sus propios cambios antes de enviar un "pull request" para que los cambios sean revisados e integrados.

- **Características**:
  - Cada desarrollador tiene su propia copia del repositorio.
  - Los cambios se integran a través de "pull requests".
  - Evita la modificación directa del repositorio principal.

- **Ventajas**:
  - Ideal para proyectos públicos donde se busca mantener un control estricto sobre qué cambios se integran.
  
#### b. Centralized Workflow

Este flujo de trabajo simula el tradicional modelo centralizado de control de versiones (como SVN), donde todos los desarrolladores trabajan directamente en una sola rama, a menudo `main` o `master`.

- **Características**:
  - Todos los colaboradores hacen `push` y `pull` directamente en la rama principal.
  - No hay un control estricto sobre las ramas individuales.

- **Ventajas**:
  - Simple de implementar y adecuado para equipos pequeños.
  
- **Desventajas**:
  - Riesgo de conflictos y problemas si varios desarrolladores están trabajando simultáneamente.

#### c. GitFlow

GitFlow es un flujo de trabajo avanzado que utiliza varias ramas para organizar el desarrollo. Es particularmente adecuado para proyectos grandes con ciclos de desarrollo formales.

- **Características**:
  - Usa ramas dedicadas para `feature`, `release` y `hotfix`.
  - Cada rama tiene un propósito claro: `develop` para desarrollo activo, `main` para lanzamientos estables.
  
- **Ventajas**:
  - Permite una gestión muy estructurada del desarrollo y lanzamientos.
  
- **Desventajas**:
  - Requiere más esfuerzo para la administración de ramas.
  - Puede ser excesivo para proyectos pequeños o simples.

## Ejercicios

### En solitario

1. Clonar el repositorio de `progit` en español y generar el libro en PDF.
2. Crear un repositorio remoto con ficheros creados por la plataforma ( `README` y `LICENSE` ) en GitHub y clonarlo en local.
2. Añadir un fichero con algo de texto y sincronizarlo con el repositorio recién clonado.

### Por parejas (trío en caso de impares)

Cada miembro de la pareja (o trío, en su caso) deberá:

1. Crear un repositorio remoto vacío en GitHub llamado  `moby-git` y sincronizarlo con el repo local homónimo.
2. Añadir al otro compañero como colaborador del repositorio y a continuación pedirle que lo clone, modifique algún fichero en la rama principal y sincronice de nuevo.
3. Sincronizar en local los cambios efectuados por el otro compañero:
    - En caso de haber conflictos, arreglarlos.
    - En otro caso, simular un escenario en el que sí los haya, acordándolo con el compañero (e.g., modificando ambos la misma línea después de hacer `push` el creador del repo y `pull` el/los colaboradores).
4. Sincronizar con remoto la resolución de los conflictos y pedirle al compañero que sincronice de nuevo, modifique algún fichero en una rama nueva y sincronice de nuevo.
5. Sincronizar los cambios del compañero y hacer `merge` de su rama creada con la principal en local. Resolver conflictos si los hubiese.
6. Repetir todos los ejercicios anteriores con GitLab.

### Bonustrack

1. Hacer un `fork` de un proyecto en GitHub de un compañero y *pushear* alguna modificación al repositorio *forkeado*.
2. Hacer un `pull request` a un proyecto en GitHub de un compañero y que este lo acepte o rechace.
3. Implementar una política de GitFlow en un repositorio propio en GitLab y hacer las operaciones necesarias para simular el ciclo completo de creación y despliegue de al menos una `feature` y un `hotfix`.

## Recursos

- [Skills Github](https://skills.github.com/)
- [Git History](https://githistory.xyz/)
