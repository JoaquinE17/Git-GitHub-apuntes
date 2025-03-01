GIT 
=====================
   - Es un sistema de control de verciones
   - Ayuda a realizar un seguimiento de los cambios de codigo
   - Se utiliza para colaborar en el codigo
 * Ejemplo en codigo:
~~~
 		1|	git --version	
		2|	git version 2.30.2 windows.1
~~~
 En el codigo, se puede ver comandos de entrada(1) y la salida(2) que este produce.
  ### GIT Y REPOSITORIOS REMOTOS
   - Git y GitHub son cosas diferentes
   - Nos enfocaremos en GitHub

  ### GIT Y GITHUB - INTRODUCCION
   
   * Que es GIT?
   Git es un popular sistema de control de verciones. Fue creado por Linus Torvalds en 2005, y ha sido mantenido por Junio Hamano desde entonces.
   * Se utiliza para:
   		- Seguimiento de cambios de codigo
   		- Seguimiento de quien hizo llos cambios
   		- Colaboracion en la codificacion
   * Que hace GIT?:
   		- Gestionar proyectos con **REPOSITORIES**
   		- **CLONE** un proyecto para trabajar en una copia local
   		- Controla y rastrea los cambios con **STAGING** y **COMMITTING** 
   		- **BRANCH** y **MERGE** permite trabajar en diferentes partes y verciones de un proyecto
   		- **PULL** traer una copia local de la ultima vercion del proyecto
   		- **PUSH** enviar actualizaciones locales del proyecto final
   * Trabajando con GIT:
   		+ Inicializa _GIT_ en una carpeta, convirtiendolo en un *REPOSITORIO*
   		+ _GIT_ ahora crea una carpeta oculta para realizar un seguimiento de los cambios en esa carpeta
   		+ Cuado se _cambia, agrega o elimina_ un archivo, se considera *MODIFICADO*
   		+ Selecciona los archivos modificados que deseas mandar al *STAGE*
   		+ Los archivos en el *STAGE* se hacen *COMMIT*, lo que solicita a _GIT_ que almacene una captura instanteana de los archivos
   		+ _GIT_ te permite ver el historial completo de cada *COMMIT*
   		+ Puedes volver a cualquier *COMMIT* anterior 
   		+ _GIT_ no almacena una copia separada de cada archhivo en cada *COMMIT*, sino que realiza un seguimiento de los cambios realizados en cada *COMMIT*
   * Por que GIT?:
   		- Mas de 70% de los desarrollacores usan _GIT_
   		- Los desarrolladores pueden trabajar juntos desde cialquier parte del mundo
   		- Los desarrolladores pueden ver el historial completo del proyecto
   		- Los desarrolladores pueden volver a verciones anteriores de un proyecto
   * Que es GITHUB?:
   		- _GIT_ no es lo mismo que _GITHUB_ 
   		- _GITHUB_ hace herramientas que usan _GIT_
   		- _GITHUB_ es la mayos cantidada de codigo fuente del mundo y ha sido propiedad de Microsoft desde 2018

COMENZANDO CON GIT
============================================================================================================

 ### INTALAR GIT:
   Puede descargar Git gratis desde el siguiente sitio web: https://www.git-scm.com/
   > Usando _GIT_ con la linea de comando
   > Lo primero que tenemos que hacer es comprobar si _GIT_ esta correctamente instalado
~~~
		1|	git --version
		2|	git version 2.30.2.windows.1
~~~
 ### CONFIGURAR GIT:
   Ahora hazle saber a _GIT_ quien eres. Esto es importante para los sistemas de control de verciones (cada **'git commit'** utiliza esta informacion)
~~~
		1|	git config --global user.name "my-name"
		2|	git config --global user.email "my@name.com"
~~~
   Cambie el nombre de usuario y la dirección de correo electrónico a la suya. Probablemente también desee usar esto al registrarse en _GitHub_ más tarde.
  
   > [Nota] : Usar global para establecer el nombre de usuario y el correo electrónico para cada repositorio en tu computadora. Si desea establecer el nombre de usuario/correo electrónico solo para el repositorio actual, puede eliminar global.

 ### CREACION DE CARPETA GIT:
   Ahora, vamos acrear una nueva carpeta para nuestro proyecto
~~~
		1|	mkdir myproject
		2|	cd myproject
~~~

 ### INICIALIZAR GIT:
   Una vez que haya navegado a la carpeta correcta, puede inicializar _GIT_ en esa carpeta
~~~
		1|	init
		2|	Initialized empty Git repository in /Users/user/myproject/.git/
~~~
   > [Nota] : _GIT_ ahora sabe que debe  mirar la carpeta que lo inicio. _GIT_ crea una carpeta oculta para realizar un seguimiento de los cambios

NUEVOS ARCHIVOS GIT
============================================================================================================

  ### AÑADIENDO NUEVOS ARCHIVOS
   Acabas de crear tu primer repositorio local de _GIT_. Pero está vacio
   Así que agreguemos algunos archivos o creemos un nuevo archivo usando su editor de texto favorito. Luego guárdelo o muévalo a la carpeta que acaba de crear.
   >> Ejemplo:
   > Usaremos un archivo html, llamado "index.html"
~~~
html:
^^^^^
  <!DOCTYPE html>
  <html>
  <head>
  <title>Hello World!</title>
  </head>
  <body>
  
  <h1>Hello world!</h1>
  <p>This is the first file in my new Git Repo.</p>
  
  </body>
  </html>
~~~
   > Volvamos a la terminal y enumeremos los archivos en nuestro directorio de trabajo actual
~~~
		1|	ls
		2|	index.html
~~~
   > Luego revisamos el **'git status'** y ver si es parte de nuestro repositorio:
~~~
		1|	git status
		2|	On branch master
		3|
		4|	NO commits yet
		5|
		6|	Untracked files:
		7|	(use "git add ..." to include in what will be committed)
		8|		index.html
		9|
	   10|	nothing added to commit but untracked files present (use "git add" to track)
~~~
   Ahora _GIT_ es **CONSCIENTE** del archivo, pero no lo ha agregado a nuestro repositorio
   Los archivos en su carpeta de repocitorio de git pueden estar en dos estados:
   * RASTREADOS: archivos que _GIT_ conoce y se agregan al repositorio
   * SIN RASTREAR: archivos que estan en su directorio de trabajo, pero no se agrgan al repositorio
   Cuando agrega archivos por primera vez a un repositorio vacío, todos estan sin rastrear. Para que Git los rastree, debe organizarlos o agregarlos al entorno de puesta en escena.


GIT STAGE 
============================================================================================================

  ### ENTORNO PRE-COMPROMETIDO - GIT STAGING
   Una de las funciones centrales de git son los conceptos ***[STAGE]*** y ***[COMMIT]***.
   A medida que trabaja puede estar agregando, editando y eliminando archivos. Pero cada vaz que termina una parte del trabajo, debe agregar el archivo a un _STAGE_.
   En esta etapa (_STAGE_) los archivos estan listos para ser comprometidos (_COMMIT_) al repocitorio en el que se esta trabajamdo.
   > Trabajamos con el archivo "index.html"-, lo añadiremos al _STAGE_:
~~~
    1|  git add index.html
~~~
   > El archivo ahora debe estar en el entorno _STAGE_ listo para el _COMMIT_, se representa de color verde. Si esto no es asi se vera de color rojo:
~~~
    1|  git status
    2|  On branch master
    3|  
    4|  No commits yet
    5|
    6|  Changes to be committed
    7|    (use "git rm --cached ..." to untage)
    8|      new file: index.html
~~~
  ### AÑADIR MAS DE UN ARCHIVO - GIT STAGING
   Tambien puede crear mas de un archivo a la vez.
   > Ahora agregaremos 2 archivos mas a nuestra carpeta de trabajo
   Un archivo llamado "README.md" describe el repositorio (todos los repositorios deben contener este tipo de archivo)
   1. Creamos README.md:
~~~
Markdown:
^^^^^^^^^
  # Hola-mundo 
  Hola Mundo es us repositorio para GIT tutorial
  This is an example repository for the GIT tutorial on https://www.w3schools.com
  
  This repository is built step by step in the tutorial.
~~~
   2. Hacemos una hoja de estilo (bluestyle.css):
~~~
css:
^^^^
  body {
    background-color: ligtblue;
  }
  h1 {
    color: navy;
    margin-left: 20px;
  }
~~~
   3. Agregamos la hoja de estilo al _html_:
~~~
html:
^^^^^
  <!DOCTYPE html>
  <html>
  <head>
  <title>Hello World!</title>
  <link rel="stylesheet" href="bluestyle.css">
  </head>
  <body>
  
  <h1>Hello world!</h1>
  <p>This is the first file in my new Git Repo.</p>
  
  </body>
  </html>
~~~
   > Ahora agregue todos los archivos del directorio actual al _STAGE_ 
~~~
    1|  git add --all
~~~
   Usando --all en lugar de nombres de archivos individuales, se suben al _STAGE_ todos los cambios (archivos nuevos, modificados y eliminados)
~~~
    1|  git status
    2|  On branch master
    3|
    4|  No commits yet
    5|
    6|  Changes to be commited:
    7|    (use "git rm --cached ..." to unstage)
    8|      new file: README.md
    9|      new file: bluestyle.css 
   10|      new file: index.html
~~~
   Ahora los tres archivos agregados al _STEGE_ estan litos para ser  _COMMIT_. 
   El comando  "git add --all" es igual a escribir "git add -A"


GIT COMMIT
============================================================================================================
   Una vez que hemos terminado con nuetro trabajo, estamos listos para pasar de _STEGE_ a _COMMIT_ para nuetro repositorio.
   Añadir _COMMITS_ mantiene un registro de nuestro progreso y cambios a medida que trabajamos. **GIT** considera cada _COMMIT_ como un punto de cambio ó punto guardado. Es un punto del proyecto al que puedes volver si encuentras un error o quieres hacer un cambio.
   > Cuando hacemos un commit, siempre deberiamos incluir un mensaje.
   Añadiendo mensajes claros a cada commit, es facil para ti, y para los demas, ver que a cambiado y cuando.
~~~
    1|  git commit -m "First release of Hello World!"
    2|  [master (root-commit) 221ec6e] First release of Hello World!
    3|    3 files changed, 26 insertions(+)
    4|    create mode 100644 README.md
    5|    create mode 100644 bluestyle.css
    6|    create mode 100644 index.html
~~~
   El comando "commit" realiza un _COMMIT_ y el "-m [mensaje]" añade un mensaje.
   El entorno de _STAGE_ ha sido enviado a nuestro repositorio, con el mensaje: ["First release of Hello World!"]
   En otras palabras los archivos PRE-COMPROMETIDOS en el _STAGE_ pasan a ser COMPROMETIDOS en el _COMMIT_.
  ### GIT COMMIT SIN STAGE
   A veces, cuando haces pequeños cambios, usar el entorno _STAGE_ parece una perdida de tiempo. En GIT es posible confirmar los cambios directamente, saltandose el entorno _STAGE_.
   La opcion "-a" prepara automaticamente todos los archivos modificados y rastreados.
   > Vamos a añadir una pequeña actualizacion a "index.html":
~~~
html:
^^^^^
  <!DOCTYPE html>
  <html>
  <head>
  <title>Hello World!</title>
  <link rel="stylesheet" href="bluestyle.css">
  </head>
  <body>
  
  <h1>Hello world!</h1>
  <p>This is the first file in my new Git Repo.</p>
  <p>A new line in our file!</p>
  
  </body>
  </html>
~~~
   > Ahora comprobaremos el estado de nuestro repositorio. Pero esta vez, usaremos la opcion "--short" para ver los cambios de una forma mas compacta:
~~~
    1|  git status --short
    2|  M index.html
~~~
  - - -
   >> NOTA: Las banderas de estado son:
   + [??]: ARCHIVOS_NO_RASTREADOS
   + [A]: ARCHIVOS_AGREGADOS_AL_STAGE_
   + [M]: ARCHIVOS_MODIFICADOS
   + [D]: ARCHIVOS_ELIMINADOS
  - - -
   Vemos que el archivo que esperabamos esta modificado. Asi que hagamos el _COMMIT_ directamente:
~~~
    1|  git commit -a -m "Updated index.html with a new line"
    2|  [master 09f4acd] Update index.html with a new line
    3|    1 file changed, 1 insertion(+)
~~~
   Advertencia:
   -----------
   > Por lo general, no se recomienda omitir el entorno _STAGE_. Saltarce este paso a veces puede hacer que incluya cambios no deseados.

  ### GIT COMMIT LOG:
   Para ver el historial de _COMMITS_ de un repositorio, puede usar el comando log:
~~~
    1|  git log
    2|  commit 09f4acd3f8836b7f6fc44ad9e012f82faf861803 (HEAD -> master)
    3|  Author: w3schools-test 
    4|  Date:   Fri Mar 26 09:35:54 2021 +0100
    5|  
    6|      Updated index.html with a new line
    7|  
    8|  commit 221ec6e10aeedbfd02b85264087cd9adc18e4b26
    9|  Author: w3schools-test 
   10|  Date:   Fri Mar 26 09:13:07 2021 +0100
   11|  
   12|      First release of Hello World!
~~~

GIT HELP
============================================================================================================
  ### AYUDA DE GIT (help)
   Si tienes problemas para recordar comandos u opciones para comandos, puedes usar "git help".
   * Hay un par de formas diferentes en que puede usar el comando _help_  en la linea de comandos:
    - 'git command -help' : para ver todas las opciones disponibles para el comando especifico
    - 'git help --all' : para ver todo los comandos disponibles
   > Repasemos los diferentes comandos:

   #### 'git -help': Para ver opciones de un comando especifico
    Cada vez que necesite ayuda para recordar la opcion especifica para un comando puedes usar 'git <<c/comando>> -help'
    >[NOTA] : Tambien puedes usar '--help' en lugar de 'help' para abrir el manual de _GIT_. 
    > Por ejemplo:
~~~
git commit -help
usage: git commit [] [--] ...

    -q, --quiet           suppress summary after successful commit
    -v, --verbose         show diff in commit message template

Commit message options
    -F, --file      read message from file
    --author      override author for commit
    --date          override date for commit
    -m, --message 
                          commit message
    -c, --reedit-message 
                          reuse and edit message from specified commit
    -C, --reuse-message 
                          reuse message from specified commit
    --fixup       use autosquash formatted message to fixup specified commit
    --squash      use autosquash formatted message to squash specified commit
    --reset-author        the commit is authored by me now (used with -C/-c/--amend)
    -s, --signoff         add a Signed-off-by trailer
    -t, --template 
                          use specified template file
    -e, --edit            force edit of commit
    --cleanup       how to strip spaces and #comments from message
    --status              include status in commit message template
    -S, --gpg-sign[=]
                          GPG sign commit

Commit contents options
    -a, --all             commit all changed files
    -i, --include         add specified files to index for commit
    --interactive         interactively add files
    -p, --patch           interactively add changes
    -o, --only            commit only specified files
    -n, --no-verify       bypass pre-commit and commit-msg hooks
    --dry-run             show what would be committed
    --short               show status concisely
    --branch              show branch information
    --ahead-behind        compute full ahead/behind values
    --porcelain           machine-readable output
    --long                show status in long format (default)
    -z, --null            terminate entries with NUL
    --amend               amend previous commit
    --no-post-rewrite     bypass post-rewrite hook
    -u, --untracked-files[=]
                          show untracked files, optional modes: all, normal, no. (Default: all)
    --pathspec-from-file 
                          read pathspec from file
    --pathspec-file-nul   with --pathspec-from-file, pathspec elements are separated with NUL character
~~~
   #### 'git -help': Ver todos los comandos posibles
   Para listar todos los comandos posibles utilice el comando 'git help --all'
~~~
$ git help --all
See 'git help ' to read about a specific subcommand

Main Porcelain Commands
   add                  Add file contents to the index
   am                   Apply a series of patches from a mailbox
   archive              Create an archive of files from a named tree
   bisect               Use binary search to find the commit that introduced a bug
   branch               List, create, or delete branches
   bundle               Move objects and refs by archive
   checkout             Switch branches or restore working tree files
   cherry-pick          Apply the changes introduced by some existing commits
   citool               Graphical alternative to git-commit
   clean                Remove untracked files from the working tree
   clone                Clone a repository into a new directory
   commit               Record changes to the repository
   describe             Give an object a human readable name based on an available ref
   diff                 Show changes between commits, commit and working tree, etc
   fetch                Download objects and refs from another repository
   format-patch         Prepare patches for e-mail submission
   gc                   Cleanup unnecessary files and optimize the local repository
   gitk                 The Git repository browser
   grep                 Print lines matching a pattern
   gui                  A portable graphical interface to Git
   init                 Create an empty Git repository or reinitialize an existing one
   log                  Show commit logs
   maintenance          Run tasks to optimize Git repository data
   merge                Join two or more development histories together
   mv                   Move or rename a file, a directory, or a symlink
   notes                Add or inspect object notes
   pull                 Fetch from and integrate with another repository or a local branch
   push                 Update remote refs along with associated objects
   range-diff           Compare two commit ranges (e.g. two versions of a branch)
   rebase               Reapply commits on top of another base tip
   reset                Reset current HEAD to the specified state
   restore              Restore working tree files
   revert               Revert some existing commits
   rm                   Remove files from the working tree and from the index
   shortlog             Summarize 'git log' output
   show                 Show various types of objects
   sparse-checkout      Initialize and modify the sparse-checkout
   stash                Stash the changes in a dirty working directory away
   status               Show the working tree status
   submodule            Initialize, update or inspect submodules
   switch               Switch branches
   tag                  Create, list, delete or verify a tag object signed with GPG
   worktree             Manage multiple working trees
   ...

~~~

GIT BRANCH
============================================================================================================
   ### TRABAJANDO CON GIT BRANCH:
   En _GIT_ un ***BRANCH*** es una vercion Nueva y separada del repositorio prinsipal.
   > Digamos que tiene un pryecto grande y necesita actualizar el diseño en el.
   > Como funcionaria eso sin y con git:
   1. Sin git:
        - Haga copias de todos los archivos relevantes para evitar impactar la vercion original.
        - Comience a trabajar con el diseño y encuentre que el codigo depende del codigo de otro archivo, que tambien deben ser cambiados.
        - Tambien haga copias de los archivos dependientes. Asegurandose de que cada archivo dependiente hace referencia al nombre del archivo correcto.
        - ERROR: Hay un error no relacionado en otro lugar del proyecto que necesita ser arreglado.
        - Guarde todos sus archivos, tomando nota de los nombres de las copias que fueron trabajados.
        - Trabaje en el error no relacionado y actualisa el codigo para solucionarlo.
        - Vuelva al diseño y termine el trabajo alli
        - Copie el codigo o cambieel nombre de los archivos, por lo que el diseño actualizado esta en la vercion original
        - 2 semanas despues, te das cuenta de que el error no relacionado no se soluciono en la nueva vercion del diseño porque copio los archivos antes de la solucion.
   2. Con git:
        - Con una nueva rama llamada "nuevo diseño"  edite el codigo directamente sin impacto a la rama principal.
        - ERROR: Hay un error no relacionado en otro lugar del proyecto que ¡necesita ser arreglado.
        - Cree una nueva rama del progecto principal llamado "small-error-flx"
        - Arregle  el error no relacionado y fucione la rama "small-error-flx" con la rama principal.
        - Vuelves a la rama de nuevo diseño y terminas el trabajo allí
        - Combine la rama de "nuevo diseño" con la principal (alertándose del pequeño error arreglado)
    Las _BRANCH_ le permiten trabajas en diferentes partes de un proyecto sin afectar la rama principal
    Cuando se cmpleta el trabajo, se puede fucionar una rama con el proyecto principal.
    Incluso puede cambiar entre _BRANCH_ y trabajar en diferentes proyectos sin interferir entre ellos.
    El ramificado en _GIT_ es muy ligero y rapido.
   ### NUEVA BRANCH EN GIT: 
   Añada algunas caracteristicas nuevas a la pagina index.html
   Estamos trabajando en nuestro repositorio local, y no queremos perturbar o destruir el proyecto prinsipal.
   > Entonces creamos un nuevo 'branch':
~~~
        1|  git branch hello_world-images
~~~
   > Confirmemos que hemos creado un nuevo 'branch'
~~~
        1|  git branch
        2|      hello-world-images
        3|  * master
+ El * al lado del master especifica que actualmente estamos en esa 'branch'
~~~
   > El comando 'checkout' es utilizado para comprobar un 'branch'. Moviendonos de la rama, a la rama especificada
~~~
        1|  git checkout hellow-world-images
        2|  Switched to branch 'hello-world-images'
+ Ahora hemos movido nuestro espacio de trabajo actual de la rama master a la nueva rama
~~~
   > Para este ejemplo agregaremos una imagen (img1.png) a la carpeta de trabajo y una linea de codigo en el archivo 'index.html'
~~~
html:
^^^^^
    <!DOCTYPE html>
    <html>
    <head>
    <title>Hello World!</title>
    <link rel="stylesheet" href="bluestyle.css">
    </head>
    <body>
    
    <h1>Hello world!</h1>
    <div><img src="img_hello_world.jpg" alt="Hello World from Space"
    style="width:100%;max-width:960px"></div>
    <p>This is the first file in my new Git Repo.</p>
    <p>A new line in our file!</p>
    
    </body>
    </html>
~~~
   > Ahora compruebe el estado del 'branch':
~~~
        1|  git status
        2|  On branch hello-world-images
        3|  Changes not staged for commit:
        4|    (use "git add ..." to update what will be committed)
        5|    (use "git restore ..." to discard changes in working directory)
        6|          modified:   index.html
        7|  
        8|  Untracked files:
        8|    (use "git add ..." to include in what will be committed)
       10|          img_hello_world.jpg
       11|  
       12|  no changes added to commit (use "git add" and/or "git commit -a
* Hay cambios en 'index.html', pero el archivo no esta en el COMMIT
* 'img_hello_world.jpg' no esta rastreado
~~~
   > Deberemos agregar ambos archivos al entorno _STAGE_ para este 'branch':
~~~
        1|  git add --all
* Usando '--all' en lugar de nombres de archivos individuales, todos los archivos modificados (nuevos, modificados y eliminados)
~~~
   > Compruebe el status de la 'branch':
~~~
        1|  git status
        2|  On branch hello-world-images
        3|  Changes to be committed:
        4|    (use "git restore --staged ..." to unstage)
        5|      new file: img_hello_world.jpg
        6|      modified: index.html
~~~
   > Estamos conforme con los cambios. Asi que haremos _COMMIT_ al 'branch' actual:
~~~
        1|  git commit -m "Added image to Hello World"
        2|  [hello-world-images 0312c55] Added image to Hello World
        3|  2 files changed, 1 insertion(+)
        4|  create mode 100644 img_hello_world.jpg
~~~
   > Ahora hay un nuevo 'branch', pero diferente del 'branch' master:
   > [NOTA] : Usando la opcion '-b' en 'checkout' (_checkout -b_) creara una nueva rama, y se movera a ella, si no existe
   ### CAMBIO ENTRE RAMAS (branch):
   Ahora veamos qué tan rápido y fácil es trabajar con diferentes ramas y qué tan bien funciona.
   Actualmente estamos en el BRANCH 'hello-world-images'. Agregamos una imagen a esta rama, listemos los archivos del directorio actual
~~~
        1|  ls
        2|  README.md  bluestyle.css  img_hello_world.jpg  index.html
* Podemos ver el nuevo archivo 'img_hello_world.jpg', y si abrimos el archivo 'index.html', podemos ver que el código ha cambiado. 
~~~
   > Ahora, veamos que sucede cuando cambiamos a la rama master
~~~
        1|  git checkout master
        2|  Switched to branch 'master'
* La nueva imagen no es parte de esta rama. 
~~~
   > Listamos los archivos del directorio actual nuevamente
~~~
        1|  ls
        2|  README.md  bluestyle.css  index.html
* La 'img_hello_world.jpg' no existe. Y si abrimos el archivo index.html, podemos ver el código revertido a lo que era antes de la alteración.
~~~
   ### RAMA DE EMERGENCIA:
   Ahora imagine que aun no hemos terminado con las imagenes de hola mundo, pero necesitamos corrregir un error en la rama master.
   No quiero meterme en la rama _master_ directamente, y no quiero meterme a la rama hello-world-images, ya que aun no se ha hecho.
   Asi que creamos una nueva rama (BRANCH) para hacer frente a la emergencia:
~~~
        1|  git checkout -b emergecy-fix
        2|  Switches to a new branch 'emergency-fix'
~~~
   Ahora hemos creado una nueva rama de la rama _master_, y nos hemos cambiamos a ella. Podemoscorrejir el error de forma segura sin molestar a las otras ramas.
   > Arreglamos nuestro error imaginario:
~~~
html:
^^^^^
    <!DOCTYPE html>
    <html>
    <head>
    <title>Hello World!</title>
    <link rel="stylesheet" href="bluestyle.css">
    </head>
    <body>
    
    <h1>Hello world!</h1>
    <p>This is the first file in my new Git Repo.</p>
    <p>This line is here to show how merging works.</p>
    
    </body>
    </html>
~~~
   > Hemos realizado cambios en este archivo, y nesecitamos obtener esos cambios en la rama _master_. Verifique el estado:
~~~
        1|  git status
        2|  On branch emergency-fix
        3|  Changes not staged for commit:
        4|    (use "git add ..." to update what will be committed)
        5|    (use "git restore ..." to discard changes in working directory)
        6|          modified:   index.html
        7|  
        8|  no changes added to commit (use "git add" and/or "git commit -a")
~~~
   > Agregelos al _STAGE_ y despues al _COMMIT_:
~~~
        1|  git add index.html
        2|  git commit -m "Update index.html whiht emergency fix"
        3|  [emergency-fix dfa79db] updated index.html with emergency fix
        4|   1 file changed, 1 insertion(+), 1 deletion(-)
~~~
   > Ahora estamos lista la solucion para la rama master, y necesitamos fucionar las dos ramas

GIT MERGE
============================================================================================================
   ### FUSIONAR RAMAS
   Tenemos una solucion una rama de emrgencia, asi que fucionemos la ramas (_maste_ y _emergency-fix_)
   > Primero necesitamos cambiar a la rama _master_:
~~~
        1|  git checkout master
        2|  Switched to branch 'master'
~~~
   > Ahora fusionamos la rama actual (_master_) con la rama _emergency-fix_:
~~~
        1|  git merge emergency-fix
        2|  Updating 09f4acd..dfa79db
        3|  Fast-forward
        4|   index.html | 2 +-
        5|   1 file changed, 1 insertion(+), 1 deletion(-)
~~~
   Dado que la rama _emergency-fix_ provenia directamente de _master_, y no se habian realizado otros cambios de dominio mietras estabamos trabajando, _GIT_ ve esto como una continuacion de la rama _master_. Por lo tanto, puede avanzar rapido, simplemente señalando tanto el _master_ como _emergency-fix_ a la misma configuracion.
   > Como la rama _master_ y _emergency-fix_ son esesencialmente los mismos ahora, podemos eliminar _emergency-fix_, ya que ya no es necesaria:
~~~
        1|  git branch -d emergency-fix
        2|  Deleted branch emergency-fix (was dfa79db).
~~~
   ### FUSIONAR CONFLICTO 
   Ahora podemos pasar a 'hello-world-images' y seguir traabajando. Añade otro archivo de imagen (img2-git.png) y cambia index.html, para que lo  muestre:
~~~
        1|  git checkout hellow-world-images
        2|  Switched to branch 'hello-world-images'
~~~
   > Modificar html:
~~~
html:
^^^^^
    <!DOCTYPE html>
    <html>
    <head>
    <title>Hello World!</title>
    <link rel="stylesheet" href="bluestyle.css">
    </head>
    <body>
    
    <h1>Hello world!</h1>
    <div><img src="img_hello_world.jpg" alt="Hello World from Space" style="width:100%;max-width:960px"></div>
    <p>This is the first file in my new Git Repo.</p>
    <p>A new line in our file!</p>
    <div><img src="img_hello_git.jpg" alt="Hello Git" style="width:100%;max-width:640px"></div>
    
    </body>
    </html>
~~~
   > Ahora, hemos terminado con nuestro trabajo aqui y puede pasarlo al _STAGE_ y hacer un _COMMIT_

~~~
        1|  git add --all
        2|  git commit -m "added new image"
        3|  [hello-world-images 1f1584e] added new image
        4|   2 files changed, 1 insertion(+)
        5|   create mode 100644 img_hello_git.jpg
~~~
   > Vemos que 'index.html' hasido cambiado en ambas ramas. Ahora estamos listos para fusionar la rama 'hello-world-images' en la rama 'master'. Pero, que pasara con los cambios que hemos hecho recientemente en la rama master?
~~~
        1|  git checkout master
        2|  git merge hellow-world-images
        3|  Auto-merging index.html
        4|  CONFLICT (content): Merge comflict in index.html
        5|  Automatic merge failed; fix conflicts and then commit the result.
~~~
   > La fucion fallo, ya que hay un conflicto entre las verciones para index.html. Comprobemos el estado:
~~~
        1|  git status
        2|  On branch master
        3|  You have unmerged paths
        4|  (fix conflicts and run "git commit")
        5|    (use "git merge --abort" to abort the merge)
        6|  
        7|  Changes to be committed:
        8|          new file:   img_hello_git.jpg
        9|          new file:   img_hello_world.jpg
       10|  
       11|  Unmerged paths:
       12|  (use "git add ..." to mark resolution)
       13|         both modified:   index.html
~~~
   Esto confirma que hay un conflicto en index.html, pero los archivos de imagen estan listos y preparados para realizar _COMMIT_
   > Asi que tenemos que arreglar ese conflicto. Habra el archivo en nuestro editor:
~~~
<!DOCTYPE html>
<html>
<head>
<title>Hello World!</title>
<link rel="stylesheet" href="bluestyle.css">
</head>
<body>

<h1>Hello world!</h1>
<div><img src="img_hello_world.jpg" alt="Hello World from Space" style="width:100%;max-width:960px"></div>
<p>This is the first file in my new Git Repo.</p>
<<<<<<< HEAD
<p>This line is here to show how merging works.</p>
=======
<p>A new line in our file!</p>
<div><img src="img_hello_git.jpg" alt="Hello Git" style="width:100%;max-width:640px"></div>
>>>>>>> hello-world-images

</body>
</html>
~~~
   > Podemos ver las diferencias entre las verciones y editarlo como queramos:
~~~
<!DOCTYPE html>
<html>
<head>
<title>Hello World!</title>
<link rel="stylesheet" href="bluestyle.css">
</head>
<body>

<h1>Hello world!</h1>
<div><img src="img_hello_world.jpg" alt="Hello World from Space" style="width:100%;max-width:960px"></div>
<p>This is the first file in my new Git Repo.</p>
<p>This line is here to show how merging works.</p>
<div><img src="img_hello_git.jpg" alt="Hello Git" style="width:100%;max-width:640px"></div>

</body>
</html>
~~~
   > Ahora podemos pasar 'index.html' al _STAGE_ y comprobar el estado:
~~~
        1|  git add index.html
        2|  git status
        3|  On branch master
        4|  All conflicts fixed but you are still merging.
        5|    (use "git commit" to conclude merge)
        6|  
        7|  Changes to be committed:
        8|          new file:   img_hello_git.jpg
        9|          new file:   img_hello_world.jpg
       10|          modified:   index.html
~~~
   > El conflicto se ah solucionado, y podemos utilizar _COMMIT_ para concluir la fusion:
~~~
        1|  git commit -m "merged with hello-world-images after fixing conflicts"
        2|  [master e0b6038] merged with hello-world-images after fixing conflicts
~~~
   > Y 'git branch -d' para eliminar la rama hello-world-images:
~~~
        1|  git branch -d hello-world-images
        2|  Deleted branch hello-world-images (was 1f1584e).
~~~
  > Ahora compruebe mejor como funcionan las ramas y la fusion.
  > Es hora de empezar a trabajar con un repositorio remoto
