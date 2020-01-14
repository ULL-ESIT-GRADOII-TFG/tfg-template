# TFG de Andrés Calimero García Pérez

## Instruciones Generales para el Uso de este Repo

### Instrucciones para clonar los repos

Siga estos pasos:

Clone el repo principal:

```
[/tmp]$ git clone git@github.com:PAL-ULL/tfg-andres-calimero.git
Cloning into 'tfg-andres-calimero'...
remote: Enumerating objects: 29, done.
remote: Counting objects: 100% (29/29), done.
remote: Compressing objects: 100% (19/19), done.
remote: Total 29 (delta 13), reused 24 (delta 8), pack-reused 0
Receiving objects: 100% (29/29), done.
Resolving deltas: 100% (13/13), done.
```

Sitúese en la carpeta del repo:

```
[/tmp]$ cd tfg-andres-calimero/
```

Supongo que tiene node.js instalado. Ejecute:

```
[/tmp/tfg-andres-calimero(master)]$ npm run init
```
Esto debería sincronizar los sub módulos produciendo una salida como esta:

```
> tfg-andres-calimero@1.0.0 init /private/tmp/tfg-andres-calimero
> git submodule init && git submodule update

Submodule 'tfg-andres-calimero-memoria' (git@github.com:PAL-ULL/tfg-andres-calimero-memoria.git) registered for path 'tfg-andres-calimero-memoria'
Submodule 'tfg-andres-calimero-software' (git@github.com:PAL-ULL/tfg-andres-calimero-software.git) registered for path 'tfg-andres-calimero-software'
Cloning into '/private/tmp/tfg-andres-calimero/tfg-andres-calimero-memoria'...
Cloning into '/private/tmp/tfg-andres-calimero/tfg-andres-calimero-software'...
Submodule path 'tfg-andres-calimero-memoria': checked out 'b4c91ce3a50ff038713430d804983fd5cb68b6f5'
Submodule path 'tfg-andres-calimero-software': checked out '8dad8a54d408b64afa6a143509d0e20375ddc997'
```

Si no hay fallos, la estructura que le quede debería ser similar a esta:

```
[/tmp/tfg-andres-calimero(master)]$ tree
~/.../TFG/tfg-andres-calimero-garcia-perez(master)]$ tree
.
├── README.md
├── tfg-andres-calimero-memoria
│   └── README.md
└── tfg-andres-calimero-software
    └── README.md
```

### [Tablero Kanban para seguimiento del proyecto](https://github.com/PAL-ULL/tfg-andres-calimero-memoria/projects/1) 

En este tablero se establecen las reuniones, incidencias y objetivos globales al TFG

* [Tablero Kanban para seguimiento del proyecto](https://github.com/PAL-ULL/tfg-andres-calimero/projects/1) 
* [Acerca de los tableros de proyecto](https://help.github.com/es/github/managing-your-work-on-github/about-project-boards)

Posiblemente deberíamos considerar la posiblidad de tableros Kanban independientes para la memoria y el software

### Tareas definidas en package.json

Para facilitarle la labor he dejado algunas tareas de control de versiones en el `package.json`:

```
[~/.../TFG/tfg-andres-calimero(master)]$ npm run
Scripts available in tfg-andres-calimero via `npm run-script`:
  pull-sub
    git submodule foreach --recursive 'git pull origin master'
  push-sub
    npm run commit-sub; git submodule foreach --recursive 'git push origin master'
  init
    git submodule init && git submodule update
  commit-sub
    git submodule foreach --recursive 'git commit -am working || :'
  push
    git commit -am working && git push
```

#### Pull all subrepos

```
[~/.../TFG/tfg-andres-calimero(master)]$ npm run pull-sub

> tfg-andres-calimero@1.0.0 pull-sub /Users/casiano/local/src/TFG/tfg-andres-calimero
> git submodule foreach --recursive 'git pull origin master'

Entering 'tfg-andres-calimero-memoria'
From github.com:PAL-ULL/tfg-andres-calimero-memoria
 * branch            master     -> FETCH_HEAD
Already up to date.
Entering 'tfg-andres-calimero-software'
From github.com:PAL-ULL/tfg-andres-calimero-software
 * branch            master     -> FETCH_HEAD
Already up to date.
```

#### Commit all sub repos

```
[~/.../TFG/tfg-andres-calimero(master)]$ npm run commit-sub

> tfg-andres-calimero@1.0.0 commit-sub /Users/casiano/local/src/TFG/tfg-andres-calimero
> git submodule foreach --recursive 'git commit -am working || :'

Entering 'tfg-andres-calimero-memoria'
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
Entering 'tfg-andres-calimero-software'
On branch master
Your branch is up to date with 'origin/master'.
```

### Para Aprender mas sobre Submódulos Git

En muchas ocasiones es necesario tener junto a nuestro repo de proyecto otros repos de otros proyectos.
Por ejemplo, cuando hacemos un paquete para npm es conveniente tener junto al repo del paquete un segundo 
repositorio con un cliente que nos sirva para probar el correcto uso del paquete en producción. 
Esto nos lleva a veces a crear 
un macro-repo que contiene los  repos acoplados.

* [Chacon's book on Git: Chapter 7.11 Git Tools - Submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules)

Este repo contiene dos submódulos:

```
[~/.../TFG/tfg-andres-calimero(master)]$ git submodule 
 443c98999fcd68b883b622d92068c5aba7f20a5c tfg-andres-calimero-memoria (heads/master)
 8dad8a54d408b64afa6a143509d0e20375ddc997 tfg-andres-calimero-software (heads/master)
```

#### Ejemplo de uso de submódulos

* [Ejemplo en https://github.com/ULL-ESIT-DSI-1617/create-a-npm-module](https://github.com/ULL-ESIT-DSI-1617/create-a-npm-module)
  - [Submódulo https://github.com/ULL-ESIT-DSI-1617/scapegoat](https://github.com/ULL-ESIT-DSI-1617/scapegoat)
  - [Submódulo https://github.com/ULL-ESIT-DSI-1617/prueba-scapegoat](https://github.com/ULL-ESIT-DSI-1617/prueba-scapegoat)[