# 1. Introducción a Git y control de versiones
- [Conceptos básicos del control de versiones](#conceptos-básicos-del-control-de-versiones)
- [Historia y características de Git](#historia-y-características-de-git)
- [Instalación y configuración inicial de Git](#instalación-y-configuración-inicial-de-git)
- [Diferencias entre SCV centralizados y distribuidos](#diferencias-entre-scv-centralizados-y-distribuidos)

## Conceptos básicos del control de versiones

El control de versiones es una metodología esencial en el desarrollo de software que permite gestionar los cambios en el código a lo largo del tiempo. Algunos conceptos clave incluyen:

- **Versiones**: Cada cambio realizado en un archivo o conjunto de archivos queda registrado como una versión. Esto permite retroceder a versiones anteriores si se cometen errores.
- **Repositorio**: El lugar donde se almacenan todas las versiones de los archivos. Puede ser local (en tu máquina) o remoto (en un servidor compartido).
- **Colaboración**: El control de versiones permite que varios desarrolladores trabajen simultáneamente en un proyecto sin interferir en el trabajo de otros, gestionando y resolviendo los conflictos de manera eficiente.
- **Integridad**: El control de versiones garantiza que los cambios se registren de manera confiable y que el historial de cambios esté disponible en todo momento.

## Historia y características de Git

### ¿Qué es Git y cómo funciona?

Git es un sistema distribuido de control de versiones que permite a múltiples desarrolladores trabajar en paralelo en diferentes partes de un proyecto sin riesgo de pérdida de información. Su funcionamiento se basa en:

- **Instantáneas (Snapshots)**: Git no rastrea las diferencias línea por línea como SVN, sino que toma una instantánea de cómo está el proyecto en un momento dado. Si no hay cambios, simplemente referencia la versión anterior.
- **Eficiencia**: Gracias a su arquitectura distribuida, las operaciones comunes como commit, branch, merge y pull son extremadamente rápidas.
- **Concurrencia**: Git facilita el trabajo colaborativo, ya que permite la creación y fusión de ramas sin afectar el trabajo en curso de otros colaboradores.
- **Integridad**: Git garantiza la integridad de los datos con un hash SHA-1, lo que asegura que cada commit sea único y no se pueda modificar sin dejar rastro.

### ¿Por qué usarlo?

- Git permite a los desarrolladores trabajar en paralelo de forma efectiva, evitando conflictos y facilitando la gestión de múltiples versiones del código.
- Su enfoque distribuido elimina la dependencia de un servidor central, mejorando la resiliencia y flexibilidad.
- El manejo de ramas y fusiones es muy eficiente, ideal para equipos que trabajan en múltiples características simultáneamente.

## Instalación y configuración inicial de Git

- Git está disponible para varias plataformas: Linux, macOS y Windows.
- En sistemas basados en Debian, se instala con el comando:

  ```bash
  sudo apt install git
  ```
- En macOS, puedes usar Homebrew:

  ```bash
  brew install git
  ```
- En Windows, puedes instalar Git desde [git-scm.com](https://git-scm.com).

## Diferencias entre SCV centralizados y distribuidos

- **SVN (Subversion)**: SVN es un sistema de control de versiones centralizado. Esto significa que el código se almacena en un servidor central, y los desarrolladores trabajan con una copia local. Aunque ha sido muy popular, su enfoque centralizado presenta limitaciones en comparación con Git.
  - **Pros de SVN**: 
    - Más fácil de entender para principiantes.
    - Buenas herramientas gráficas y soporte en muchas IDEs.
  - **Contras de SVN**:
    - La dependencia de un servidor central puede ser un problema si este falla.
    - Fusiones y ramas suelen ser complicadas.

- **Git**: Git es un sistema de control de versiones distribuido, lo que significa que cada desarrollador tiene una copia completa del historial del proyecto. Git permite mayor flexibilidad y velocidad, especialmente en proyectos de gran escala y con equipos distribuidos.
  - **Pros de Git**:
    - Cada clon de un repositorio es completo, sin dependencia continua de un servidor central.
    - Ramas y fusiones son rápidas y eficientes.
    - Historia clara de los cambios y más opciones de reversión y manejo de errores.
  - **Contras de Git**:
    - Curva de aprendizaje más pronunciada.
    - La flexibilidad puede ser abrumadora para equipos sin experiencia.

- **Otras alternativas**:
  - **Mercurial**: Otro sistema de control de versiones distribuido, menos popular que Git, pero con un enfoque en simplicidad.
  - **Perforce**: Un sistema centralizado utilizado en grandes empresas, especialmente en videojuegos.

## Recursos

- [Subversion migration](https://training.github.com/downloads/es_ES/subversion-migration/)
- [Install Git on Windows](https://zaycodes.medium.com/how-to-install-git-on-windows-f6031afef08c)
