REGLAS DE [.gitignore] 
==========================

1. Las lineas en blanco se ignoran.  

2. Las lineas comenzadas con '#' se ignoran:  
	> [Ejemplo] : # texto_comentado  

3. Todos los archivos con nombre 'name', carpetas con nombre 'name' y archivos y carpetas de cualquier carpeta con nombre 'name'.  
	> [Ejemplo] : name --> /name.log , /name/file.txt , /lib/name.log  

4. La terminacion con '/' especifica que el patron es para una carpeta. Coincide con todos los archivos y carpetas de cualquier carpeta de nombre 'name'.  
	> [Ejemplo] : name/ --> /name/log/name.log , /name/log/name.log  

5. Todos los archivos llamados 'name.file':  
	> [Ejemplo] : name.file --> /lib/name.file , /name.file  

6. Los archivos comenzados por '/' espesifica que el patron solo coincide con los archivos de la carpeta raiz.
	> [Ejemplo] : /name.file  

7. Los patrones que especifican archivos en carpetas especificas son siempre relativos a root (incluso si no empiezan por '/').  
	> [Ejemplo] : lib/name file

8. Empezar con ' ** ' antes de '/' espesifica que coincide con culquier carpeta del repositorio. No solo de la raiz.
	> [Ejemplo] : '** / lib / name.file' --> /test/lib/name.file , /test/lib/name.file  

9. Todas las carpetas con nombre 'name' y los archivos y carpetas de cualquier carpeta con nombre 'name'.  
	> [Ejemplo] : '** / name' --> /name/log.file , /lib/name/log.file , /name/lib/log.file  

10. Todas las carpetas con nombre 'name' y los archivos y carpetas de cualquier carpeta de nombre 'name' dentro de la carpeta 'lib'.  
	> [Ejemplo] : '/ lib / ** /name' --> /lib/name/log.file , /lib/test/name/log.file  

11. Todos los archvos con la extencion '.file':  
	> [Ejemplo] : '* .file' --> /name.file , /lib/name.file  

12. Todas las carpetas terminadas con 'name':  
	> [Ejemplo] : '* name/' --> /lastname/log.file , /firstname/log.file  

13. '?' Coincide con un unico caracter no especifico:  
	> [Ejemplo] : name?.file --> /names.file , /name1.file  

14. '[rango]' coincide con un unico caracter del rango especificado (en este caso, un caracter del rango a-z, y tambien puede ser numerico).  
	> [Ejemplo] : name[a-z].file --> /named.file , /namey.file  

15. '[conjunto]' coincide con un unico caracter del conjunto de caracteres especificado (en este caso a,b,c):  
	> [Ejemplo] : name[abc].file --> /namea.file , /namec.file  

16. '[!conjunto]' coincide con un unico caracter excepto los especificados en el conjunto de caracteres (en este caso a,b,c):  
	> [Ejemplo] : name[!abc].file --> /names.file , /namex.file  

17. '!' especifica una negacion o exepcion. Coincide con todos los archivos y carpetas de cualquier carpeta 'name', exepto 'name/secret.log':  
	> [Ejemplo] : name/ !name/secret.log --> /name/file.txt , /name/log/name.log  

18. '!' especifica una negacion o excepcion. Todos los archivos con la extencion '.file', excepto 'name.file':  
	> [Ejemplo] : '* .file' !name.file --> /log.file , /lastname.file  

19. Si se añaden nuevos patrones despues de una navegacion, se volvera a ignorar un archivo negado anteriormente. Todos los archivos con extencion '.file', exepto los de la carpeta 'name' a menos que el nombre del archivo sea junk.
	> [Ejemplo] : '* .file' '!name/* .file' ' junk.* ' --> /log.file , /name/log.file
