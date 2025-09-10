# Git - sistema de control de versiones

## Trabajo previo

### Tutoriales

Abba, I. V. (2021). *Git and GitHub Tutorial – Version Control for Beginners*. FreeCodeCamp.Org. https://www.freecodecamp.org/news/git-and-github-for-beginners/

### Otros

Instale en su computadora el sistema de control de versiones [Git](https://git-scm.com/downloads).

## Descripción general

[Git](https://git-scm.com/) es un sistema de [control de versiones](https://es.wikipedia.org/wiki/Control_de_versiones) diseñado para "rastrear" cambios en el código fuente durante el proceso de desarrollo de software. Sin embargo, puede ser utilizado para llevar el control de los cambios en cualquier conjunto de archivos (ej. [documentación](https://guides.github.com/features/wikis/), [música](https://techcrunch.com/2013/10/09/splice-music/)).

Un sistema de control de versiones proporciona, entre otras ventajas:

* La capacidad de recuperar versiones anteriores de los archivos.
* La capacidad de integrar modificaciones efectuadas por varias personas en el mismo conjunto de archivos.
* La capacidad de mantener varias "ramas" (_branches_) de un producto (ej. "estable", "evaluación", "inestable", como en el caso de [Debian Linux](https://www.debian.org/releases/), [GRASS GIS](https://grass.osgeo.org/download/software/sources/) y muchos otros proyectos de software libre).
* Facilidades para mantener redundancia y respaldos de los archivos (ej. [Programa de respaldos de GitHub](https://archiveprogram.github.com/)). Esta es una facilidad que implementan algunos servicios en la nube.

Git fue diseñado por Linus Torvalds en 2005 durante del desarrollo del _kernel_ del sistema operativo Linux. Se caracteriza por ser un [sistema de control de versiones distribuido](https://es.wikipedia.org/wiki/Control_de_versiones_distribuido), lo que significa que el código fuente puede estar alojado en la estación de trabajo de cualquier miembro del equipo de desarrollo. No se requiere de un repositorio "central", pero también se puede trabajar de esa forma.

El protocolo de Git es utilizado en varios sitios que proveen servicios de alojamiento de software, entre los que están [SourceForge](https://sourceforge.net/), [Bitbucket](https://bitbucket.org/), [GitLab](https://about.gitlab.com/) y [GitHub](https://github.com/).

## Funcionamiento

Desde el punto de vista de un usuario de Git (ej. un programador), Git se utiliza para sincronizar la versión local (i.e. en la computadora personal del usuario) de un conjunto de archivos, llamado proyecto o repositorio, con la versión que está alojada en un sistema remoto (ej. GitHub). Cada repositorio se almacena en un directorio (carpeta) del sistema operativo. La sincronización se realiza principalmente a través de dos operaciones:

- **_push_**: para "subir" al repositorio remoto los cambios realizados en el repositorio local. Esta operación se realiza mediante el comando [git push](https://git-scm.com/docs/git-push). Es probable que el sistema remoto le solicite al usuario algún tipo de autenticación (ej. nombre de usuario y clave).
- **_pull_**: para "bajar" al repositorio local los cambios realizados en el repositorio remoto. Esta operación se realiza mediante el comando [git pull](https://git-scm.com/docs/git-pull).

Las operaciones _push_ y _pull_ se ilustran en la {numref}`figure-git-push-pull`.

```{figure} img/git-push-pull.png
:name: figure-git-push-pull

Operaciones _push_ y _pull_. Imagen de [Melinda Higgins](https://www.coursera.org/learn/reproducible-templates-analysis/lecture/NGbQv/git-and-github-part-1).
```

Antes de un _push_, el usuario debe seleccionar los archivos que desea subir mediante el comando [git add](https://git-scm.com/docs/git-add), el cual pasa los archivos a un "área de espera" (_staging area_). Luego debe usarse el comando [git commit](https://git-scm.com/docs/git-commit) para "guardar" los cambios pendientes en el área de espera. Cada _commit_ guarda el estado del conjunto de archivos en un momento específico (_snapshot_).

La relación entre estas operaciones de Git, se ilustra en la {numref}`figure-git-push-pull-commit`.

```{figure} img/git-push-pull-commit.png
:name: figure-git-push-pull-commit

Operaciones de Git. Imagen de [Steven Klavins](https://medium.com/@stevenklavins94/version-control-part-4-c9387cf5b33e).
```

En la {numref}`figure-git-stage-commit-push` se muestra el funcionamiento de Git mediante una comparación con el procesamiento de una compra en línea.

```{figure} img/git-stage-commit-push.png
:name: figure-git-stage-commit-push

Operaciones de Git y compras en línea. Imagen de [Melinda Higgins](https://www.coursera.org/learn/reproducible-templates-analysis/lecture/NGbQv/git-and-github-part-2).
```

Otras operaciones de Git de uso frecuente son:

* [git config](https://git-scm.com/docs/git-config): para especificar opciones globales de la sesión de Git (ej. nombre del usuario, dirección de corre electrónico).
* [git init](https://git-scm.com/docs/git-init): para inicializar un repositorio git.
* [git clone](https://git-scm.com/docs/git-clone): para clonar (i.e. copiar) un repositorio remoto en la computadora local.
* [git status](https://git-scm.com/docs/git-status): para revisar el estado de los archivos y, por ejemplo, saber cuales deben pasarse al área de espera.
* [git log](https://git-scm.com/docs/git-log): para revisar el historial de _commits_.
* [git show](https://git-scm.com/docs/git-show): para visualizar los cambios efectuados en los _commits_.
* [git reset](https://git-scm.com/docs/git-reset): para regresar al estado correspondiente a un _commit_ anterior.

## Recursos de interés

*Git*. (s. f.). Recuperado 28 de agosto de 2022, de https://git-scm.com/

*GitHub Archive Program*. (s. f.). GitHub Archive Program. Recuperado 10 de abril de 2022, de https://archiveprogram.github.com/

Higgins, M. (s. f.). *Reproducible Templates for Analysis and Dissemination*. Coursera. Recuperado 11 de abril de 2022, de https://www.coursera.org/learn/reproducible-templates-analysis

Klavins, S. (2020). *Version Control part 1*. Medium. https://stevenklavins94.medium.com/version-control-part-1-c5f1b43127f6
