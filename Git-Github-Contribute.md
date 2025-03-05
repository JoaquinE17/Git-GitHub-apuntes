GITHUB CONTRIBUTE
=====================
 ## GITHUB FORK  
  ### AÑADIR AL REPOSITORIO DE OTRA PERSONA:  

   En el corazon de git está la colaboracion. Sin embargo, Git no te permite añadir codigo al repositorio de otra persona sin derechos de acceso.  
   Despues de lo que aprenderas a continuacion podras copiar un repositorio, hacer cambios en él, y sugerir que esos cambios se implementen en el repositorio original.  

  ### FORK (bifurcar) UN REPOSITORIO:  

   Un **fork** es una copia de un repositorio. Esto es útil cuando quieres contribuir al proyecto de otra persona o empezar tu propio proyecto basado en el suyo.  
   **Fork** no es un comando de _Git_, sino algo que se ofrece en _GitHub_ y otros hosts de repositorios. Empecemos iniciando sesión en GitHub, y bifurkemos (fork) nuestro repositorio:  
    	https://github.com/JoaquinE17/prueba  
   Ahora tenemos nuestra propia copia de 'prueba' en Github. Veamos como añadir una copia local de esto para que podamos trabajar con ella.  

 ## GIT CLONE PARA GITHUB  
  ### CLONAR UN FORK (bifurcacion) DESDE GITHUB:  
   Ahora tenemmos nuestro propio **fork**, pero solo en _GitHub_. Tambien queremos un **clon** en nuestro _Git_ local para seguir trabajando en él.  
   **Clone** es una copia completa de un repositorio, incluyendo todos los registros y versiones de los archivos.  
   Vuelve al repositorio original, haz click en el boton verde 'code' para obtener la URL para clonar.  

   * Abre tu Git-bash y clona (_clone_) el repositorio:  

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

   > [NOTA] : Para especificar una carpeta concreta a la que clonar, añade nombre de la carpeta despues de la URL  del repositorio:  
   git clone https://github.com/ejemplo-prueba/ejemplo-prueba myfolder  


   * Navegue hasta el nuevo directorio y compruebe el estado:  

   ~~~ bash:
        cd ejemplo-prueba
        git status
        . On branch master
        . Your branch is up to date with 'origin/master'.

        . nothing to commit, working tree clean
   ~~~  

   * Y comprueba el registro para confirmar que tenemos los datos completos del repositorio:  

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

  ### CONFIGURACION REMOTA:  
   Básicamente, tenemos una copia completa de un repositorio, en cuyo origen no se nos permite hacer cambios.  
   Veamos cómo se configura remotamente desde _Git_.  

   ~~~ git:
        1|  git remote -v
        2|  origin  https://github.com/w3schools-test/w3schools-test.github.io.git (fetch)
        3|  origin  https://github.com/w3schools-test/w3schools-test.github.io.git (push)
   ~~~  

   Vemos que 'origin' está configurado para el repositorio original 'ejemplo-prueba', tambien queremos añadir nuestro propio fork.  
   En primer lugar, renombramos el original origin remote:  

   ~~~ git:
        1|  git remote rename origin upstream
        2|  git remote -v
        3|  upstream        https://github.com/w3schools-test/w3schools-test.github.io.git (fetch)
        4|  upstream        https://github.com/w3schools-test/w3schools-test.github.io.git (push)
   
   ~~~  

   A continuacion, obten la URL de nuestro propio 'fork'.  
   Y añadelo como 'origin':
   ~~~ git:
        1|  git remote add origin https://github.com/kaijim/w3schools-test.github.io.git
        2|  git remote -v
        3|  origin  https://github.com/kaijim/w3schools-test.github.io.git (fetch)
        4|  origin  https://github.com/kaijim/w3schools-test.github.io.git (push)
        5|  upstream        https://github.com/w3schools-test/w3schools-test.github.io.git (fetch)
        6|  upstream        https://github.com/w3schools-test/w3schools-test.github.io.git (push)
   ~~~  

   > [NOTA] : De acuerdo con las convenciones de nomenclatura de _Git_, se recomienda nombrar tu propio repositorio 'origin', y el que has bifurcado (fork) para 'upstream'  
   
   * Ahora tenemos 2 remotos:
    'origin' - nuestropropio fork, donde tenemos acceso de lectura y escritura
    'upstream' - el original, donde tenemos acceso de solo lectura
   Ahora vamos a hacer algunos cambios en el codigo en el codigo. Mas adelante cubriremos cómo sugerimos esos cambios al repositorio original.  
