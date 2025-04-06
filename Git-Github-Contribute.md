GITHUB CONTRIBUTE
=====================
 ## GITHUB FORK  
  ### AÑADIR AL REPOSITORIO DE OTRA PERSONA:  

   En el corazon de git está la colaboracion. Sin embargo, Git no te permite añadir codigo al repositorio de otra persona sin derechos de acceso.  
   Despues de lo que aprenderas a continuacion podras copiar un repositorio, hacer cambios en él, y sugerir que esos cambios se implementen en el repositorio original.  

  ### FORK (bifurcar) UN REPOSITORIO:  

   Un **fork** es una copia de un repositorio.  
   Esto es útil cuando quieres contribuir al proyecto de otra persona o empezar tu propio proyecto basado en el suyo.  
   **Fork** no es un comando de _Git_, sino algo que se ofrece en _GitHub_ y otros hosts de repositorios. Empecemos iniciando sesión en GitHub, y bifurkemos (fork) nuestro repositorio:  
    	https://github.com/JoaquinE17/prueba  
   Ahora tenemos nuestra propia copia de 'prueba' en Github. Veamos como añadir una copia local de esto para que podamos trabajar con ella.  

 ## GIT CLONE PARA GITHUB  
  ### CLONAR UN FORK (bifurcacion) DESDE GITHUB:  
   Ahora tenemmos nuestro propio **fork**, pero solo en _GitHub_. Tambien queremos un **clon** en nuestro _Git_ local para seguir trabajando en él.  
   **Clone** es una copia completa de un repositorio, incluyendo todos los registros y versiones de los archivos.  
   Vuelve al repositorio original, haz click en el boton verde 'code' para obtener la URL para clonar.  

   * Habre tu Git-bash y clona (_clone_) el repositorio:  

   ~~~ git:
        1|  git clone https://github.com/w3schools-test/w3schools-test.github.io.git
        2|  Cloning into 'w3schools-test.github.io'...
        3|  remote: Enumerating objects: 33, done.
        4|  remote: Counting objects: 100% (33/33), done.
        5|  remote: Compressing objects: 100% (15/15), done.
        6|  remote: Total 33 (delta 18), reused 33 (delta 18), pack-reused 0
        7|  Receiving objects: 100% (33/33), 94.79 KiB | 3.16 MiB/s, done.
        8|  Resolving deltas: 100% (18/18), done.
   ~~~  

   * Echa un vistazo a tu sistema de archivos, y verás un directorio con el nombre del proyecto clonado:  

   ~~~ bash:
        ls
        ./ prueba
   ~~~  

   > [NOTA] : Si se quiere clonar en una carpeta concreta se debe especificar el nombre de esa carpeta, añadiendo el nombre de esa carpeta despues de la URL del repositorio original, si la carpeta no existe se creara la carpeta:  
   ~~~ git:
        1|   git clone https://github.com/ejemplo-prueba/ejemplo-prueba myfolder  
   ~~~ 

   * Navegue el nuevo directorio y compruebe el estado:  

   ~~~ bash:
        cd ejemplo-prueba
        git status
        . On branch master
        . Your branch is up to date with 'origin/master'.

        . nothing to commit, working tree clean
   ~~~  

   * Y comprueba el registro (log) para confirmar que tenemos los datos completos del repositorio:  

   ~~~ git:
        1|  git log
        2|  commit facaeae8fd87dcb63629f108f401aa9c3614d4e6 (HEAD -> master, origin/1|    master, origin/HEAD)
        3|  Merge: e7de78f 5a04b6f
        4|  Author: w3schools-test 
        5|  Date:   Fri Mar 26 15:44:10 2021 +0100
        6|  
        7|      Merge branch 'master' of https://github.com/w3schools-test/hello-world
        8|  commit e7de78fdefdda51f6f961829fcbdf197e9b926b6
        9|  Author: w3schools-test 
       10|  Date:   Fri Mar 26 15:37:22 2021 +0100
       11|  
       12|      Updated index.html. Resized image
       13|      
       14|  .....
   ~~~  

   * Ahora tenemos una copia completa del repositorio original.  

  ### CONFIGURACION REMOTA (repo clonado):  
   Básicamente, tenemos una copia completa de un repositorio, cuyo repositorio 'origin' no se nos permite hacer cambios.  

   Veamos desde _Git_, cómo el repo remoto esta configurado:  

   ~~~ git:
        1|  git remote -v
        2|  origin  https://github.com/w3schools-test/w3schools-test.github.io.git (fetch)
        3|  origin  https://github.com/w3schools-test/w3schools-test.github.io.git (push)
   ~~~  

   Vemos que 'origin' está configurado para el repositorio original *w3schools-test*, pero ahora queremos añadirlo a nuestro propio fork (copia del repo original).  

   En primer lugar, renombramos el repositorio remoto original ['origin' -> 'upstream']:  

   ~~~ git:
        1|  git remote rename origin upstream
        2|  git remote -v
        3|  upstream        https://github.com/w3schools-test/w3schools-test.github.io.git (fetch)
        4|  upstream        https://github.com/w3schools-test/w3schools-test.github.io.git (push)
   
   ~~~  

   A continuación, obten la URL de nuestro propio 'fork' *github.com/kaijim...* (copia del repo original) NO del original  
   Y añadelo como 'origin':  

   ~~~ git:
        1|  git remote add origin https://github.com/kaijim/w3schools-test.github.io.git
        2|  git remote -v
        3|  origin  https://github.com/kaijim/w3schools-test.github.io.git (fetch)
        4|  origin  https://github.com/kaijim/w3schools-test.github.io.git (push)
        5|  upstream        https://github.com/w3schools-test/w3schools-test.github.io.git (fetch)
        6|  upstream        https://github.com/w3schools-test/w3schools-test.github.io.git (push)
   ~~~  

   > [NOTA] : De acuerdo con las convenciones de nomenclatura de _Git_, se recomienda nombrar tu propio repositorio como 'origin', y el que has bifurcado (fork) como 'upstream' (repo original)  
   
   * Ahora tenemos 2 repositorios remotos:  
     - 'origin' - [*github.com./kaijim/...*] nuestro propio fork, donde tenemos acceso de lectura y escritura  
     - 'upstream' - [*github.com/w3schools-test/...*] el original, donde solo tenemos acceso de lectura
       
   Ahora vamos a hacer algunos cambios en el codigo. Mas adelante cubriremos cómo sugerimos esos cambios al repositorio original.  

 ## GITHUB ENVIAR UNA PULL REQUEST
  ### ENVIAR CAMBIOS A NUESTRO GITHUB FORK:
   Hemos hecho un monton de cambios en nuestro _Git_ local.  
   Confirma los cambios:  
   Ahora haremos PUSH a nuestro _GitHub Fork_:  

   ~~~ git:
          1|  git push origin
          2|  Enumerating objects: 8, done.
          3|  Counting objects: 100% (8/8), done.
          4|  Delta compression using up to 16 threads
          5|  Compressing objects: 100% (5/5), done.
          6|  Writing objects: 100% (5/5), 393.96 KiB | 32.83 MiB/s, done.
          7|  Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
          8|  To https://github.com/kaijim/1 w3schools-test.github.io.git
          9|     facaeae..ebb1a5c  master -> master
   ~~~

   * Vamos a _GitHub_, y vemos que el repositorio tiene un nuevo 'commit'. Y podemos enviar una _Pull Request_ al repositorio original (contribute).  

   * Haz click en él, y crea una _Pull Recuest_.  

   * Recuerda añadir una explicación detallada de tus cambios para que los administradores sepan de que se trata.  

   * Envia esa _Pull Recuest_.  

  ### APROBANDO UNA PULL REQUEST:
   Ahora cualquier miembro con acceso puede ver el _Pull Request_ cuando vea el repositorio original.  

   * Pueden ver los cambios propuestos. Comentar los cambios y fusionar. Confirma. Y los cambios se fusionaran con la rama _master_ (repositorio original).