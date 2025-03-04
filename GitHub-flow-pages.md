GITHUB FLOW
=====================
 ## TRABAJAR CON GITHUB FLOW
  GitHub Flow es un flujo de trabajo diseñado para funcionar bien con Git y GitHub.
  Se centra en la creacion de ramas y hace posible que los equipos experimenten libremente y realicen despliegues con regularidad.
  **GITHUB FLOW FUNCIONA DE LA SIGUIENTE MANERA:**
   1. Crear nueva rama 
   2. Hacer cambios y añadir _commits_
   3. Abrir una _Pull Request_
   4. Revisar
   5. Desplegar
   6. Fusionar
  Ya deberias tener una comprension de como funciona esto. A continuacion entenderas como _FLOW_ facilita el trabajo en conjunto.
  ### CREAR UNA NUEVA RAMA:
  	La ramificacion es un concepto clave en _Git_. Funciona alrededor de la regla de que la rama _master_ es SIEMPRE desplegable.
  	Eso significa que si quieres probar algo nuevo, o experimentar, tienes 	que crear una nueva rama. La creacion de ramas te proporciona un entorno en el que puedes hacer cambios sin afectar a la rama principal.
  	Cuando tu nueva rama esta lista, puede ser revisada, discutida y 	fucionada con la rama principal cuando este lista.
  	Cuando creas una nueva rama, (casi siempre) querras hacerlo desde la rama master. 
  	 > [NOTA] : Ten en cuenta que estas trabajando con otras personas.	 Utiliza nombres descriptivos para las nuevas ramas, asi todo el mundo podra entender lo que esta pasando.
  ### HACER CAMBIOS Y AÑADIR COMMITs:
    Una vez creada la nueva rama, es hora de ponerse manos a la obra. Haz cambios añadiendo, editando y borrando archivos. Cada vez que alcances un pequeño hito, añade los cambios a tu rama mediante _commit_.
    Añadir _commits_ mantiene un registro de tu trabajo. Cada confirmacion (COMMIT) debe tener un mensaje que explique que ha cambiado y por qué. Cada _commit_ se convierte en parte de la historia de la rama, y en un punto al que puedes volversi lo necesitas.
     > [NOTA] : Los mensajes en los _commits_ son muy importantes. Permite que todo el mundo sepa qué ha cambiado y por qué. Los mensajes y comentarios facilitan mucho el seguimiento de los cambios, tanto para ti como para los demas. 
  ### ABRIR UNA PULL REQUEST:
    La _pull request_ es una parte clave de GitHub. Una _Pull Request_ notifica a la gente que tiene cambios listos para que los conderen o revisen.
    Puedes pedir a otros que revisen tus cambios o que extraigan tu contribucion y la fusionen en su rama.
  ### REVISAR (review):
    Cuando se hace un _Pull Request_,  puede ser revisado por quien tenga el acceso apropiado a la rama. Aqui es donde ocurren las buenas discuciones y la revicion de cambios.
     > Los _Pull Request_ estan diseñados para permitir a la gente trabajar juntos facilmente y producir mejores resultados juntos.
    Si recibes Feedback y continuas mejorando tus cambios, puedes empujar tus cambios con nuevos _commits_, haciendo posibkes mas reviciones.
     > [NOTA] : GitHub muestra las nuevas confirmaciones (COMMITs) y comentarios en _'unfied Pull Request view'_.
  ### DESPLEGAR (deploy):
    Cuando la _Pull Request_ ha sido revisada y todo parece correcto, es el momento de las pruebas finales en produccion antes de fusionarla con la rama _master_.
    Si surge algun problema, puedes deshacer los cambios desplegando de nuevo la rama _master_ en produccion.
     > [NOTA] : Los equipos suelen tener entornos de prueba dedicados para desplegar ramas.
  ### FUSIONAR (merge):
    Despues de realizar pruebas exhaustivas, puedes fusionar el codigo en la rama _master_.
    La _Pull Request_ guardan registros de los cambios en tu codigo, y si comentaste y nombraste bien los cambios, puedes volver atras y entender por qué se hicieron los cambios y tomaron esas decisiones.
     > [NOTA] : Puedes añadir palabras clave a tu _Pull Request_ para facilitar la busqueda.

GITHUB PAGES
=====================
