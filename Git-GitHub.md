GIT y GITHUB
=====================
 ## COMENZANDO CON GITHUB
   Crear una cuenta en GitHub:
   > Entra a https://github.com y create una cuenta (sign up)
   Recuerda utilizar la misma direccion de correo electronico que utilizo en la configuracion de git.

   ### CREAR UN REPOSITORIO EN GITHUB:
   > Ahora que ya tienes una cuenta en GitHuub, inicia sesion y crea un nuevo repocitorio.
   > Llene los datos pertinentes
   Revisamos las diferentes opciones y lo que significan mas adelante. Pero por ahora, elija Publico (si desea que el repocitorio sea visible para cualquiera) o Privado (si desea elegir quien debe ser capaz de ver el repositorio). De cualquier manera, podras elegir quien puede contribuir al repositorio
   > A continuacion, haz click en [Crear repositorio] 

   ### PUSH AL REPOSITORIO LOCAL DE GITHUB:
   > Como ya hemos creado un repositorio Git en local, vamos a enviarlo a GitHub
   Copia la URL, o haga click en el portapapeles
   > Ahora pega el siguiente comando en la terminal:
   ~~~ git:
		1|	git remote add origin https://github.com/JoaquinE17/prueba.git
   ~~~
   * [git remote add origin URL] : Especifica que estas añadiendo un repositorio remoto, con la _URL_ especificada, como _ORIGIN_ en tu repositorio local.
   > Ahora vamos a hacer _push_ de nuetra rama _master_ a la URL de _origin_ y establecerla como la rama remota por defecto.
   Dado que es la primera vez que te conectas a GitHub, recibirás algún tipo de notificación para autenticar esta conexión.
   > Ahora, vuelve a GitHub y comprueba que el repositorio se ha actualizado.
   ~~~ git:
		1|	git push --set-upstream origin master
		2|	Enumerating objects: 22, done.
		3|	Counting objects: 100% (22/22), done.
		4|	Delta compression using up to 16 threads
		5|	Compressing objects: 100% (22/22), done.
		6|	Writing objects: 100% (22/22), 92.96 KiB | 23.24 MiB/s, done.
		7|	Total 22 (delta 11), reused 0 (delta 0), pack-reused 0
		8|	remote: Resolving deltas: 100% (11/11), done.
		9|	To https://github.com/w3schools-test/hello-world.git
	 10|	 * [new branch]      master -> master
	 11|	Branch 'master' set up to track remote branch 'master' from 'origin'.
   ~~~
   ~~~ Explicacion:    
    1. **`git push`**: Este es el comando básico de Git que se usa para subir (empujar) tus cambios locales a un repositorio remoto. Generalmente, esto sube las ramas y commits que  tienes en tu repositorio local hacia el remoto.
    
    2. **`--set-upstream`**: Este parámetro le dice a Git que, además de empujar los cambios, debe establecer una relación entre tu rama local y la rama remota correspondiente. Esto es útil cuando estás trabajando con una rama que aún no tiene una referencia remota o no está configurada para hacer `push` o `pull` por defecto.
    
    3. **`origin`**: Este es el nombre por defecto que Git le da al repositorio remoto cuando lo clonas o cuando lo configuras inicialmente. Se refiere a la ubicación de tu repositorio remoto, es decir, el servidor o servicio donde está alojado el repositorio, como GitHub, GitLab, Bitbucket, etc.
    
    4. **`master`**: Es el nombre de la rama que estás empujando. En muchos repositorios antiguos, `master` es la rama principal, aunque en algunos repositorios más nuevos ahora se usa `main` como nombre por defecto. Este comando indica que estás empujando tus cambios a la rama `master` del repositorio remoto.
    
    > ¿Qué hace el comando completo?
       Este comando empuja los cambios de la rama local `master` hacia el repositorio remoto llamado `origin` y, al mismo tiempo, establece una relación de seguimiento (upstream) entre tu rama local `master` y la rama remota `master`. Esto significa que, después de ejecutar este comando, cuando uses simplemente `git push` o `git pull` en el futuro, Git sabrá a qué rama remota se debe conectar automáticamente.
      
       Por ejemplo, si aún no habías vinculado la rama `master` a la remota, después de ejecutar este comando, ya podrás hacer `git push` sin necesidad de especificar `origin master` cada vez.
   ~~~
   Dado que es la primera vez que te conectas a GitHub, recibirás algún tipo de notificación para autenticar esta conexión.
   > Ahora, vuelve a GitHub y comprueba que el repositorio se ha actualizado.

 ## EDITAR CODIGO - GITHUB
   Editar tu codigo en GitHub:
   Ademas de almacenar el contenido de Git, Github tiene un editor de codigo muy bueno.
   > Intentemos editar el archivo README.md en GitHub. Simplemente haz click en el boton editar
   Añadir algunos cambios en el codigo, y luego confirmar (COMMIT) los cambios. Por ahora, vamos confirmar (COMMIT) a la rama _master_

 ## PULL - GITHUB
   Git pull, para estar al dia con los cambios: 
   Cuandi se trabaja en equipo en un proyecto, es importante que todo el mundo esté al dia.
   Cada vez que empieces a trabajar en un progecto, deberias obtener los cambios mas recientes en tu copia local.
   > Con GIT, puedes hacerlo con 'pull'. 'Pull' es una combinacion de dos comandos diferentes:
      * fetch
      * merge
   Veamos mas de cerca como funcionan fetch,merge y pull:
  ### GIT FETCH:
     Fetch obtiene todo el historial de cambios de una rama/repositorio. En tu git local, 'fetch' muestra las actualizaciones para ver que a cambiado en github
     ~~~ git:
     1|  git fetch origin
     2|  remote: Enumerating objects: 5, done.
     3|  remote: Counting objects: 100% (5/5), done.
     4|  remote: Compressing objects: 100% (3/3), done.
     5|  remote: Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
     6|  Unpacking objects: 100% (3/3), 733 bytes | 3.00 KiB/s, done.
     7|  From https://github.com/w3schools-test/hello-world
     8|     e0b6038..d29d69f  master     -> origin/master     
     ~~~
     > Ahora que tenemos los cambios recientes, podemos comprobar buestro estado:
     ~~~ git:
     1| git status
     2| On branch master
     3| Your branch is behind 'origin/master' by 1 commit, and can be      
     4|  fast-forwarded.
     5|   (use "git pull" to update your local branch)
     6| 
     7| nothing to commit, working tree clean
     ~~~
     > Estamos detras del origin/master por 1 commit. Ese deberia ser el README.md actualizado, pero vamos a comprobarlo viendo el log:
     ~~~ git:
     1| git log origin/master
     2| commit d29d69ffe2ee9e6df6fa0d313bb0592b50f3b853 (origin/master)
     3| Author: w3schools-test <77673807+w3schools-test@users.noreply.github.com>
     4| Date:   Fri Mar 26 14:59:14 2021 +0100
     5| 
     6|     Updated README.md with a line about GitHub
     7| 
     8| commit e0b6038b1345e50aca8885d8fd322fc0e5765c3b (HEAD -> master)
     9| Merge: dfa79db 1f1584e
    10| Author: w3schools-test 
    11| Date:   Fri Mar 26 12:42:56 2021 +0100
    12| 
    13|     merged with hello-world-images after fixing conflicts
    14| ...
    15| ...
     ~~~
     > Esto parece lo esperado, pero tambien podemos verificarlo mostrando las diferencias entre nuestra rama _master_ local y _origin/master_:
     ~~~ git:
     1| git diff origin/master
     2| diff --git a/README.md b/README.md
     3| index 23a0122..a980c39 100644
     4| --- a/README.md
     5| +++ b/README.md
     6| @@ -2,6 +2,4 @@
     7|  Hello World repository for Git tutorial
     8|  This is an example repository for the Git tutoial on https://www.w3schools.com
     9| 
    10| -This repository is built step by step in the tutorial.
    11| -
    12| -It now includes steps for GitHub
    13| +This repository is built step by step in the tutorial.
    14| \ No newline at end of file
     ~~~
     > Es exactamente como esperabamos. Ahora podemos fusionar con seguridad
  ### GIT MERGE:
     Merge fusiona la rama actual, con una rama especifica.
     Hemos confirmado que las actualizaciones son las esperadas, podemos fisionar nuestra rama actual _master_ con origin/master:
     ~~~ git:
     1| git merge origin/master
     2| Updating e0b6038..d29d69f
     3| Fast-forward
     4|  README.md | 4 +++-
     5|  1 file changed, 3 insertions(+), 1 deletion(-)
     ~~~
     > Compruebe de nuevo el estado (_status_) para confirmar que estas actualizado:
     ~~~ git:
     git status
     1| On branch master
     2| Your branch is up to date with 'origin/master'.
     3| 
     4| nothing to commit, working tree clean
     ~~~
     > Listo, tu git local esta actualizado.
  ### GIT PULL:
     Pero que pasa si solo quieres actualizar tu repositorio local, sin pasar por todos estos pasos.
     Pull es una combinacion de *fetch* y *merge*. Se utiliza para extraer todos los cambios de un repositorio remoto a la rama en la que estas trabajando.
     > Haz otro cambio en el archivo README.md en github.
     > Y utiliza 'pull' para actualizar tu git local:
     ~~~ git:
     1| git pull origin
     2| remote: Enumerating objects: 5, done.
     3| remote: Counting objects: 100% (5/5), done.
     4| remote: Compressing objects: 100% (3/3), done.
     5| remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
     6| Unpacking objects: 100% (3/3), 794 bytes | 1024 bytes/s, done.
     7| From https://github.com/w3schools-test/hello-world
     8|    a7cdd4b..ab6b4ed  master       -> origin/master
     9| Updating a7cdd4b..ab6b4ed
    10| Fast-forward
    11|  README.md | 2 ++
    12|  1 file changed, 2 insertions(+)
     ~~~
     > Asi es como mantienes tu Git local actualizado desde un repositorio remoto. Maas adelante, veras mas de cerca como funciona push en github

 ## PUSH - GITHUB
   Push - cambios en github:
   Vamos a intentar hacer algunos cambios en nuestro git local y enviarlos (_PUSH_) a GitHub:
   ~~~ html:
   <!DOCTYPE html>
   <html>
   <head>
   <title>Hello World!</title>
   <link rel="stylesheet" href="bluestyle.css">
   </head>
   <body>
   
   <h1>Hello world!</h1>
   <div><img src="img_hello_world.jpg" alt="Hello World from Space" style="width:100%;max-width:640px"></div>
   <p>This is the first file in my new Git Repo.</p>
   <p>This line is here to show how merging works.</p>
   <div><img src="img_hello_git.jpg" alt="Hello Git" style="width:100%;max-width:640px"></div>

   </body>
   </html>
   ~~~
   > Confirma (_COMMIT_) los cambios:
   ~~~ git:
   1| git commit -a -m "Updated index.html. Resized image"
   2| [master e7de78f] Updated index.html. Resized image
   3|  1 file changed, 1 insertion(+), 1 deletion(-)
   ~~~
   > Y verifica el estado:
   ~~~ git:
   1| git status
   2| On branch master
   3| Your branch is ahead of 'origin/master' by 1 commit.
   4|   (use "git push" to publish your local commits)
   5| 
   6| nothing to commit, working tree clean
   ~~~
   > Ahora envia (_PUSH_) nuestros cambios a nuestra rama remota _origin_:
   ~~~ git:
   1| git push origin
   2| Enumerating objects: 9, done.
   3| Counting objects: 100% (8/8), done.
   4| Delta compression using up to 16 threads
   5| Compressing objects: 100% (5/5), done.
   6| Writing objects: 100% (5/5), 578 bytes | 578.00 KiB/s, done.
   7| Total 5 (delta 3), reused 0 (delta 0), pack-reused 0
   8| remote: Resolving deltas: 100% (3/3), completed with 3 local objects.
   9| To https://github.com/w3schools-test/hello-world.git
  10|    5a04b6f..facaeae  master -> master 
  ~~~
  > Ve a GitHub, y confirma que el repositorio tiene el nuevo cambio (_commit_).
 ## BRANCH - GITHUB (crear nueva rama)
   En GitHub, accede a tu repositorio y haz click en el boton de la rama _master_.
   > Ahi podras crear una nueva rama. Escribe un nombre descriptivo    ('nueva-rama-r1') y haz click en crear rama.
   > La rama deberia estar ahora creada y activada. Puedes confirmar en que rama estas trabajando, mirando el boton de la rama. Ves que ahora dice el nuevo nombre ('nueva-rama-r1') en lugar de _master_.
   > Comience a trabajar en un archivo existente en esta rama. Haga click en el archivo 'index.html' y comienza a editarlo.
   > Cuando hayas terminado de editar el archivo, puedes hacer click en la   pesstaña 'preview changes' para el resultado de los cambios realizados.
   > Si estas satisfecho con los cambios, añade un comentario que explique lo que haz hecho y haz click en confirmar cambios ('commit changes')
   Ahora tienes una nueva rama en GitHub, actualizada con algunos cambios.
 ## PULL BRANCH - GITHUB
   Extraer (pull) una rama de GitHub:
   Ahora continuamos trabajando en nuestra nueva rama en nuestro Git local.
   > Vamos a hacer _PULL_ de nuestro repositorio de GitHub de nuevo para que nuestro codigo este actualizado.
   ~~~ Git:
   1|  git pull
   2|  remote: Enumerating objects: 5, done.
   3|  remote: Counting objects: 100% (5/5), done.
   4|  remote: Compressing objects: 100% (3/3), done.
   5|  remote: Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
   6|  Unpacking objects: 100% (3/3), 851 bytes | 9.00 KiB/s, done.
   7|  From https://github.com/w3schools-test/hello-world
   8|   * [new branch]      html-skeleton -> origin/html-skeleton
   9|  Already up to date.
   ~~~
   > Ahora nuestra rama principal esta actualizada. Y podemos ver que hay una nueva rama disponible en GitHub.
   Hacer uns comprobacion rapida de estado 
   ~~~ git:
   1| git status
   2| On branch master
   3| Your branch is up to date with 'origin/master'.
   4| 
   5| nothing to commit, working tree clean
   ~~~
   Y confirmamos que ramas tenemos y donde estamos trabajando en este momento:
   ~~~ git:
   1| git branch
   2| * master
   ~~~
   Por lo tanto, no tenemos la nueva rama en nuestro Git local. Pero sabemos que esta disponible en Github. Asi que podemos utilizar la opcion 'git branch -a' para ver todas las ramas locales y remotas:
   ~~~ git:
   1| git branch -a
   2| * master
   3|   remotes/origin/html-skeleton
   4|   remotes/origin/master
   ~~~
   [NOTA] : 'git branch -r' es solo para ramas remotas
   Vemos que la rama 'html-skeleton' (nueva-rama-r1) esta disponible remotamente, pero no en nuestro git local. Vamos a comprobarlo:
   ~~~ git:
   1| git checkout html-skeleton
   2| Switched to a new branch 'html-skeleton'
   3| Branch 'html-skeleton' set up to track remote branch 'html-skeleton' from 'origin'.
   ~~~
   > Y comprueba si esta todo actualizado:
   ~~~ git:
   1| git pull
   2| Already up to date
   ~~~
   > Que ramas tenemos ahora y desde donde trabajamos:
   ~~~ git:
   1| git branch
   2| * html-skeleton
   3|   master
   ~~~
   > Ahora tu editor favorito y confirma que los cambios de la rama de GitHub se han transferido.
   Asi es como se extrae una rama de GitHub a su Git local.
 ## PUSH BRANCH - GITHUB
   Enviar una rama a GitHub:
   Vamos a tratar de crear una nueva rama local (nueva-rama-r2), y enviarla a GitHub
   > Comience por crear una rama, como lo hicimos antes:
   ~~~ git:
   git checkout -b update-readme
   Switched to a new branch 'update-readme'
   ~~~
   Y hacemos algunos cambios en el archivo README.md. Solo tiene que añadir una nueva linea.
   > Asi que ahora comprobaremos el estado de la rama actual (nueva-rama-r2):
   ~~~ git:
      1| git status
      2| On branch update-readme
      3| Changes not staged for commit:
      4|   (use "git add ..." to update what will be committed)
      5|   (use "git restore ..." to discard changes in working directory)
      6|         modified:   README.md
      7| 
      8| no changes added to commit (use "git add" and/or "git commit -a")
   ~~~
   > Vemos que README.md se modifica pero no se añade al stage:
   ~~~ git:
      1|  git add README.md
   ~~~
   > Veamos el estado de la rama (nueva-rama-r2):
   ~~~ git:
      1|  git status
      2|  On branch update-readme
      3|  Changes to be committed:
      4|    (use "git restore --staged ..." to unstage)
      5|          modified:   README.md
   ~~~
   > Estamos contentos con nuestros cambios. Asi que los confirmaremos (_commit_) en la rama:
   ~~~ git:
      1|  git commit -m "Updated readme for GitHub Branches"
      2|  [update-readme 836e5bf] Updated readme for GitHub Branches
      3|   1 file changed, 1 insertion(+)
   ~~~
   > Ahora haga PUSH a la rama (nueva-rama-r2) de nuestro repositorio Git local, a GitHub, donde todo el mundo puede ver los cambios:
   ~~~ git:
      1|  git push origin update-readme 
      2|  Enumerating objects: 5, done.
      3|  Counting objects: 100% (5/5), done.
      4|  Delta compression using up to 16 threads
      5|  Compressing objects: 100% (3/3), done.
      6|  Writing objects: 100% (3/3), 366 bytes | 366.00 KiB/s, done.
      7|  Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
      8|  remote: Resolving deltas: 100% (2/2), completed with 2 local bjects.
      9|  remote:
     10|  remote: Create a pull request for 'update-readme' on GitHub by visiting:
     11|  remote:      https://github.com/w3schools-test/hello-world/pull/new/      1|  update-readme
     12|  remote:
     13|  To https://github.com/w3schools-test/hello-world.git
     14|   * [new branch]      update-readme -> update-readme
   ~~~
   > Ve a GitHub, confirma que el repositorio tiene una nueva rama:
   En GitHub ahora podemos ver los cambios y fusionarlos con la rama master si la aprobamos.
   Si haces click en ('Compare & pull recuest'), podras ver los cambios realizados y los nuevos archivos añadidos.
    [NOTA] : Esta comparacion muestra tanto los cambios de 'nueva-rama-r2' (update-readme) como los de 'nueva-rama-r2.1' (html-skeleton) por que hemos creado la nueva rama desde 'nueva-rama-r2.1' (html-skeleton)
   > Si los cambios se ven bien, puedes seguir adelante, creando un pull request
   Un 'pull request' es la forma de proponer cambios. Puedes pedir a alguien que revise tur cambios o que extraiga tu contribucion y la fucione a su rama.
   > Como es tu propio repositorio, puedes fusionar tu 'pull request' tu mismo.
   La 'pull request' registra los cambios, lo que significa que puede revisarlos mas tarde para averiguar los cambios realizados.
   Para evitar que el repositorio se complique demaciado, puede eliminar la rama que no se utiliza haciendo click en 'delete branch'.
   Y despues de confirmar (commit) que se han incluido los cambios de la rama anterior, eliminenla.