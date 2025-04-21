# 1. Introducción

- [Fundamentos del control de versiones](#fundamentos-del-control-de-versiones)
- [Conceptos básicos e historia de Git](#conceptos-básicos-e-historia-de-git)
- [Tipos de sistemas de control de versiones](#tipos-de-sistemas-de-control-de-versiones)

## Fundamentos del control de versiones

Un sistema de control de versiones (SCV) permite gestionar los cambios que se realizan sobre un conjunto de archivos a lo largo del tiempo.

Entre sus objetivos principales están:

- Registrar qué cambios se hicieron, cuándo y por quién.
- Poder recuperar versiones anteriores de los archivos.
- Facilitar el trabajo colaborativo.
- Detectar conflictos y resolverlos de forma controlada.
- Mantener una trazabilidad completa del historial del proyecto.

La gestión de versiones es fundamental en proyectos de software donde múltiples personas trabajan en paralelo, se requiere estabilidad y evolución controlada del código, y los errores deben poder rastrearse y corregirse eficazmente.

## Conceptos básicos e historia de Git

Git fue creado en 2005 por Linus Torvalds, el creador del kernel Linux, como una herramienta libre, rápida y segura para coordinar el desarrollo del sistema operativo. Surgió tras la ruptura con BitKeeper, un sistema propietario que hasta entonces se usaba en el proyecto.

Desde entonces, Git se ha consolidado como el sistema de control de versiones más usado en la industria del software.

Algunos conceptos clave que conviene tener presentes:

- **Repositorio:** conjunto de archivos versionados junto con su historial.
- **Commit:** unidad atómica de cambio, con autoría, fecha y mensaje.
- **Branch (rama):** línea de desarrollo independiente dentro del mismo proyecto.
- **Merge (fusión):** integración de los cambios de una rama en otra.
- **HEAD:** puntero al commit actual sobre el que se está trabajando.

Git destaca por:

- Su rapidez, incluso en proyectos con miles de archivos.
- Su modelo distribuido: todos los colaboradores tienen una copia completa del historial.
- Su capacidad para ramificar y fusionar código de forma eficiente.

## Tipos de sistemas de control de versiones

Existen dos grandes modelos:

### Sistemas centralizados

Un único servidor contiene el historial oficial. Los usuarios deben conectarse a él para obtener o enviar cambios.

**Ejemplos:** CVS, Subversion (SVN)

**Ventajas:**

- Modelo simple de entender.
- Control centralizado del código.

**Inconvenientes:**

- Dependencia constante de la conexión al servidor.
- Colaboración menos flexible.

### Sistemas distribuidos

Cada desarrollador tiene una copia completa del repositorio, incluyendo todo el historial.

**Ejemplos:** Git, Mercurial

**Ventajas:**

- Trabajo offline posible.
- Sin un único punto de fallo.
- Integración más fluida en equipos grandes.

Este enfoque permite a cada persona experimentar, desarrollar y revisar cambios localmente, antes de compartirlos con el resto del equipo.
