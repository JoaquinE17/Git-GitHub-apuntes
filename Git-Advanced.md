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

   ~~~ html:
   <table class="ws-table-all notranslate">
<tbody><tr>
<th style="width:200px">Pattern</th>
<th>Explanation/Matches</th>
<th style="width:150px">Examples</th>

</tr>
<tr>
<td>&nbsp;</td>
<td>Blank lines are ignored</td>
<td>&nbsp;</td>

</tr>
<tr>
<td># <em>text comment</em></td>
<td>Lines starting with # are ignored</td>
<td>&nbsp;</td>

</tr>
  <tr>
<td><em>name</em></td>
<td>All <em>name</em> files, <em>name</em> folders, and files and folders in any
<em>name</em> folder</td>
<td>/name.log<br>/name/file.txt<br>/lib/name.log</td>

  </tr>
  <tr>
<td><em>name</em>/</td>
<td>Ending with / specifies the pattern is for a folder. Matches all files and folders in any
<em>name</em> folder</td>
<td>/name/file.txt<br>/name/log/name.log<br><br><strong>no match:</strong><br>/name.log</td>

  </tr>
  <tr>
<td><em>name</em>.<em>file</em></td>
<td>All files with the <em>name.file</em></td>
<td>/name.file<br>/lib/name.file</td>

  </tr>
  <tr>
<td><em>/name</em>.<em>file</em></td>
<td>Starting with / specifies the pattern matches only 
files in the root folder</td>
<td>/name.file<br><br><strong>no match:</strong><br>
/lib/name.file</td>

  </tr>
  <tr>
<td><em>lib/name</em>.<em>file</em></td>
<td>Patterns specifiing files in specific folders are always realative to root 
(even if you do not start with / )</td>
<td>/lib/name.file<br><br><strong>no match:</strong><br>
name.file<br>/test/lib/name.file</td>

  </tr>
  <tr>
<td>**<em>/lib/name.file</em></td>
<td>Starting with ** before / specifies that it matches any folder in the 
repository. Not just on root.</td>
<td>/lib/name.file<br>/test/lib/name.file</td>

  </tr>
  <tr>
<td>**<em>/name</em></td>
<td>All <em>name</em> folders, and files and folders in any
<em>name</em> folder</td>
<td>/name/log.file<br>/lib/name/log.file<br>/name/lib/log.file</td>

  </tr>
  <tr>
<td>/lib/**<em>/name</em></td>
<td>All <em>name</em> folders, and files and folders in any
<em>name</em> folder within the lib folder.</td>
<td>/lib/name/log.file<br>/lib/test/name/log.file<br>/lib/test/ver1/name/log.file<br>
<br><strong>no match:</strong><br>
/name/log.file</td>

  </tr>
  <tr>
<td>*.<em>file</em></td>
<td>All files withe <em>.file</em> extention</td>
<td>/name.file<br>/lib/name.file</td>

  </tr>
  <tr>
<td>*<em>name</em>/</td>
<td>All folders ending with <em>name</em></td>
<td>/lastname/log.file<br>/firstname/log.file</td>

  </tr>
  <tr>
<td><em>name</em>?.<em>file</em></td>
<td>? matches a <strong>single</strong> non-specific character</td>
<td>/names.file<br>/name1.file<br><br><strong>no match:</strong><br>
/names1.file</td>

  </tr>
  <tr>
<td><em>name</em>[a-z].<em>file</em></td>
<td>[<em>range</em>] matches a <strong>single</strong> character in the 
specified range (in this case a character in the range of a-z, and also be 
numberic.)</td>
<td>/names.file<br>/nameb.file<br><br><strong>no match:</strong><br>
/name1.file</td>

  </tr>
  <tr>
<td><em>name</em>[abc].<em>file</em></td>
<td>[<em>set</em>] matches a <strong>single</strong> character in the specified 
set of characters (in this case either a, b, or c)</td>
<td>/namea.file<br>/nameb.file<br><br><strong>no match:</strong><br>
/names.file</td>

  </tr>
  <tr>
<td><em>name</em>[!abc].<em>file</em></td>
<td>[!<em>set</em>] matches a <strong>single</strong> character, <strong>except</strong> 
the ones spesified in the set of characters (in this case a, b, or c)</td>
<td>/names.file<br>/namex.file<br><br><strong>no match:</strong><br>
/namesb.file</td>

  </tr>
  <tr>
<td>*.<em>file</em></td>
<td>All files withe <em>.file</em> extention</td>
<td>/name.file<br>/lib/name.file</td>
  </tr>
  <tr>
<td><em>name</em>/<br>!<em>name</em>/secret.log</td>
<td>! specifies a negation or exception. Matches all files and folders in any
<em>name</em> folder, except name/secret.log</td>
<td>/name/file.txt<br>/name/log/name.log<br><br><strong>no match:</strong><br>/name/secret.log</td>

  </tr>
  <tr>
<td>*.<em>file<br></em>!<em>name</em>.file</td>
<td>! specifies a negation or exception. All files withe <em>.file</em> extention, except name.file</td>
<td>/log.file<br>/lastname.file<br><br><strong>no match:</strong><br>
/name.file</td>

  </tr>
  <tr>
<td>*.<em>file<br></em>!<em>name</em>/*<em>.file</em><br>junk.*</td>
<td>Adding new patterns after a negation will re-ignore a previous negated file<br>All files withe <em>.file</em> extention, except the ones in <em>name</em> 
folder. Unless the file name is junk</td>
<td>/log.file<br>/name/log.file<br><br><strong>no match:</strong><br>
/name/junk.file</td>

  </tr>
</tbody></table>