GIT ADVANCED
=====================
 ## GIT IGNORE (.gitignore)
  Cuando compartes tu codigo con otros, a menudo hay archivos o partes de tu proyecto que no quieres compartir.  

   > [Ejemplo] : Archivos de registro, archivos temporales, archivos ocultos, archivos personales, etc.  

  _Git_ puede especificar que archivos o partes de tu proyecto deben ser ignorados por _Git_ usando un archivo llamado '.gitignore'.  
  _Git_ no rastreará los rchivos y carpetas especificadas en '.gitignore'. Sin embargo, el propio archivo '.gitignore' es rastreado por Git.  

  ### CREAR ARCHIVO '.gitignore':  
   Para crear un archivo '.gitignore' ve a la raiz de tu Git local y crealo:  

   ~~~ bash:
   		touch .gitignore
   ~~~  

   Ahora habra el archivo con un editor de texto.  
   Vamos a añadir dos reglas sencillas:  
   - Ignorar cualquier archivo con la extencion '.log'
   - Ignorar todo lo que haya en cualquier directorio llamado 'temp'  

   ~~~ gitignore:
   		# ignore ALL .log files
   		*.log

   		# ignore ALL files in ANY directory named temp
   		temp/
   ~~~  

   Ahora todos los archivos '.log' y cualquier cosa en carpetas temporales seran ignorados por Git.  

   > [NOTA] : En este caso, utilizamos un unico '.gitignore' que se aplica a todo el repositorio. Tambien es posible tener archivos '.gitignore' adicionales en subdirectorios. Estos sólo se aplican a los archivos o carpetas dentro de ese directorio.  

  ### REGLAS PARA '.gitignore':  
   Estas son las reglas generales para la busqueda de patrones en archivos '.gitignore':  

   > Ver el archivo [Git-Reglas de .gitignore][Rules_gitignore]

  #### LOCAL Y PERSONAL - GIT IGNORE - REGLAS:
   Tambien es posible ignorar archivos o carpetas pero no mostrarlo en el archivo distribuido '.gitignore'.  
   Este tipo de ignorados se especifican en el archivo '.git/into/exclude'. Funciona de la misma manera que '.gitignore' pero no se muestra a nadie mas.  

[Rules_gitignore]:./Rules_gitignore.md
