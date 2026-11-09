\# Errores de Git que me he encontrado



Guía personal con los errores que me han salido al empezar con Git y GitHub en Windows, y cómo los resolví.



\## 1. `git` no se reconoce como comando

\*\*Mensaje:\*\* `git : El término 'git' no se reconoce como nombre de un cmdlet, función, archivo de script o programa ejecutable.`



\*\*Cuándo pasa:\*\* justo después de instalar Git, en un terminal que ya estaba abierto.



\*\*Solución:\*\* cerrar todas las ventanas de PowerShell, abrir una nueva y repetir `git --version`. Si sigue igual, reiniciar el equipo.



\*\*Por qué pasa:\*\* el terminal abierto antes de instalar no conoce la ruta nueva de Git. Windows solo actualiza esa ruta en las ventanas que se abren después de la instalación.



\## 2. No es un repositorio de Git

\*\*Mensaje:\*\* `fatal: not a git repository (or any of the parent directories): .git`



\*\*Cuándo pasa:\*\* al ejecutar `git push`, `git status` o `git add` en una carpeta que no es un repositorio. A mí me pasó en `C:\\Users\\Danie`.



\*\*Solución:\*\* entrar en la carpeta del repo con `cd nombre-del-repo` y comprobar con `git status` que dice `On branch main`.



\*\*Por qué pasa:\*\* los comandos de Git solo funcionan dentro de la carpeta de un repositorio clonado o inicializado.



\## 3. Repositorio no encontrado al clonar

\*\*Mensaje:\*\* `ERROR: Repository not found. fatal: Could not read from remote repository.`



\*\*Cuándo pasa:\*\* al hacer `git clone` de un repo que no existe con ese nombre exacto en mi cuenta.



\*\*Solución:\*\* comprobar en el navegador que existe `https://github.com/mi-usuario/nombre-del-repo`. Si da 404, crearlo en GitHub con \*\*New repository\*\*. Si existe, comparar el nombre letra por letra con el del comando, o copiar la URL desde el botón verde \*\*Code\*\*.



\*\*Por qué pasa:\*\* la conexión SSH funcionaba (me pidió la passphrase), pero el repo no existía o el nombre tenía alguna letra distinta.



\## 4. Repo clonado dentro de otro repo

\*\*Cuándo pasa:\*\* al hacer `git clone` estando dentro de la carpeta de otro repositorio. A mí me pasó clonando mi web personal dentro de `lab-servidor-web`.



\*\*Solución:\*\* salir a la carpeta personal con `cd \~`, borrar la carpeta que sobra y volver a clonar. Si ya la había preparado con `git add`, deshacerlo con `git rm --cached nombre-carpeta`. Al terminar, `git status` del repo original debe decir `nothing to commit, working tree clean`.



\*\*Por qué pasa:\*\* Git clona dentro de la carpeta en la que estés en ese momento.



\*\*Cómo evitarlo:\*\* hacer siempre `cd \~` antes de cada `git clone`.



\## Mensaje que parece un error pero no lo es

\*\*Mensaje:\*\* `Hi usuario! You've successfully authenticated, but GitHub does not provide shell access.`



\*\*Cuándo sale:\*\* al probar la conexión con `ssh -T git@github.com`.



\*\*Qué significa:\*\* la clave SSH funciona y GitHub me reconoce. Que no ofrezca acceso por terminal es lo normal.



\## Comandos que me ayudan a diagnosticar

| Comando | Para qué sirve |

|---------|----------------|

| `pwd` | Ver en qué carpeta estoy |

| `dir` | Ver qué hay en la carpeta |

| `git status` | Ver el estado del repo y en qué rama estoy |

| `git branch` | Ver las ramas (la activa lleva asterisco) |

