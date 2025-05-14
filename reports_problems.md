### Reportes de problemas:  

Conflicto en git al realizar 'git pull':
--------------------------------------  

 Al intentar sincronizar los cambios locales con los cambios remotos mediante 'git pull', se produse un conflicto (merge conflict) relacionado con un archivo que se encuentra eliminado localmente pero modificado remotamente. Git no pudo resolver automaticamente esta situacion y detuvo el proceso de fusión.
 ~~~ bash
 CONFLICT (modify/delete):
 <file.example> deleted in HEAD and modified in <commit>.
 Automatic merge failed; fix conflicts and then commit the result.
 ~~~
 El estado del repositorio cambio a _MERGING_, impidiendo continuar con otras operaciones hasta resolver el conflicto.  
 
 * Accion correctiva:  
  	- Concervar el archivo remoto (cancelar el delete local):  
 	 		~~~ bash
 			git restore --source=origin/master --staged --worktree <name_file>
 			git commit -m "Conflicto resuelto: archivo remoto <name_file> concervado"
 			~~~
 	- Mantetener la eliminacion (descartar la vercion remota):  
 	 		~~~ bash
	 		git rm <name_file>
 			git commit -m "Conflicto resuelto: archivo <name_file> eliminado"
 			~~~
 * Recomendaciones:
 	- Verificar el estado del repositorio antes de hacer 'pull', especialmente si se eliminaron archivos.  
	- Considerar el uso  de 'git pull --rebase' para evitar merges innesesarios.  
	- Usar 'git status' frecuentemente para identificar conflictos a tiempo.  

