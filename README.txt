# ProyectoLDST
Proyecto para asignatura LDST

No se si llegaremos a usar esto pero creo que si lo mantenemos simple podría llegar a valer. No nos han dado mucho tiempo y encima por 
la situación parece que cada vez es más dificil quedar. Con esto podemos ir haciendo cada uno nuestra contribución de forma asíncrona según tengamos tiempo. A parte
como la que yo me se va a estar un rato confinada (o no) nos puede facilitar las cosas.

He investigado un poco sobre el tema de GitHub y todo eso (en vez de hacer FSI lmao) y voy a dejar aquí una serie de indicaciones. Siempre manteniendolo simple, pues
no nos sobra el tiempo.

----------------------------------------------------------------------------------------------------------------------------------------------------
1. INICIALIZACIÓN: clone.

Supongo que todos tenemos GitBash debido a FTR. Si estais leyendo esto es porque os he agregado a colaborar en un repositorio remoto en GitHub. Para empezar a trabajar
necesitaremos "clonar" el repositorio remoto a nuestro ordenador. En GitHub, dad al boton verde "code" y copiad la dirección HTTPS que os proporciona. Esa es la URL
del repositorio remoto.

A continuación abrid Git Bash y situaos en el directorio donde querais montar vuestro repositorio local. Clonad el respositorio local usando "git clone [URL rep. remoto]".
Con esto ya lo tenéis.

----------------------------------------------------------------------------------------------------------------------------------------------------
2. USO Y FUNCIONAMIENTO DEL REPOSITORIO LOCAL: add, commit, status.

En nuestro repositorio local podemos hacer lo que queramos. Crear nuevas carpetas, ficheros, imágenes. Podemos cambiar el código y realizar nuestras pruebas agusto.
Si usáis "git status" podéis ver el estado de las ficheros y directorios de vuestro repositorio local, veréis que los ficheros que habéis cambiado están en rojo y pone algo del tipo
"modified".

Git usa una serie de punteros que apuntan a los estados del repositorios remoto y local en distintos instantes de tiempo. De esta forma se puede llevar un control 
sobre cuáles son las diferencias entre lo que hay en lo remoto (GitHub) y en lo local (nuestro ordenador). Al hacer cambios en nuestro repositorio local, Git 
detecta que lo que hay en el respositorio local actualmente no es lo mismo que lo que indica el estado de ese mismo repositorio (se ha modificado x fichero, hay nuevos
directorios, etc).

Con "git add [fichero/directorio]" pasamos los ficheros que hayamos modificado a una fase de "staging". De esta forma indicamos a Git que estos ficheros se han modificado
y que estamos preparandonos para un nuevo "commit" (haciendo un "git status" se puede ver como los ficheros en los que ponía "modified" han pasado a "ready to commit"). 
Hacer "commit" se basa en cambiar el estado del repositorio local a lo que tenemos en este actualmente, es decir, cambiar el contenido del puntero de estado. 
Esto lo hacemos con "git commit -m ["mensaje explicativo"]", -m es un parámetro opcinional, pero si poneís que habéis modificadonos ahorramos muchos quebraderos de cabeza. 
Con esto hemos actualizamos nuestro repositorio local e incluso podemos volver a commits anteriores si queremos (estados anteriores del repositorio).

----------------------------------------------------------------------------------------------------------------------------------------------------
3. USO Y FUNCIONAMIENTO DEL REPOSITORIO REMOTO: fetch, merge, pull ,push.

Toda la parafernalia del punto anterior se refiere únicamente a nuestro repositorio local. ¿Qué pasa con el remoto?

Mantengamoslo simple, como he dicho antes, git usa punteros que apuntan a los estado del repositorio local y remoto. Imaginemos por ejemplo, que el repositorio remoto
cambia respecto al local de vuestro ordenador, pero queréis trabajar sobre lo que hay en el remoto. Con "git fetch origin" sincronizamos los punteros de nuestro repositorio
local con el del el remoto, "origin" es un alias para el repositorio remoto que nos interesa (por defecto coge ese, pero no viene mal ponerlo). Cabe destacar que 
actualizamos los DATOS, no el CONTENIDO de nuestro repositorio local (porque lo que hay en el remoto no tiene por qué ser lo mismo que en el local). Para incluir los cambios
del repositorio remoto al local usamos "git merge". Con esto Git compara el estado del repositorio local con el de el remoto y hace que queden iguales usando la información
de estado. Si por ejemplo hay un fichero que ha sido modificado, Git se encarga de hacer los cambios necesarios para que queden iguales.

"git pull origin" se encarga de hacer fetcht y merge de seguido, simplificando el proceso. A modo explicaivo dejo el siguiente esquema:

 	  A---B---C master on origin <-versiones (commits) en el repositorio remoto de GitHub.
	 /
    D---E---F---G master <-versiones (commits) en el repositorio local de tu ordenador.

Si hacemos "git pull origin" en nuestro repositorio local aparecía la versión H en nuestro repositorio local.

	  A---B---C origin/master
	 /         \
    D---E---F---G---H master


Ahora imaginemos que hemos trabajado en nuestro repositorio local y queremos incorporar los cambios al remoto. "git push origin" manda todos nuestros commits al repisotorio remoto
para que este alcance el mismo estado que el nuestro (el local). Si miramos las cosas desde el lado del servidor, es como si el repositorio remoto se sincronizara con el nuestro (fetch)
y luego se igualaran (merge).

---------------------------------------------------------------------------------------------------------------------------------------------------------
4. RAMAS.

Git usa un sistema de ramas "branches" en caso de que por ejemplo se quiera desarrollar funcionalidades de forma paralela. De hecho "merge" lo que hace es juntar ramas distintas en una sola
(de ahí que el repositorio local y remoto sean iguales con pull y push en realidad es la rama principal master y origin/master juntandose". Sin embargo, queremos mantener esto simple, y no
creo que las vayamos a usar. Solo decir que por defecto usamos la rama máster y que hay un montón de info por internet y el concepto no es muy dificil.

Si veo que puede merecer la pena o me aburro un rato a lo mejor pongo algo aquí (o lo ponéis vosotros ;) ). Aun así no creo que lo usemos.

---------------------------------------------------------------------------------------------------------------------------------------------------------

5. RESUMEN.

En conclusión:

	->Para bajar el repositorio por primera de github usa "git clone" y la URL basada en HTTPS.
	
	->Para añadir los cambios que hagas a tu repositorio local usa "git add [fichero(s)]" y luego "git commit -m ["explicacion"]".

	->Para igualar estado del repositorio remoto al tuyo local (subir tus cambios) usa "git push origin".

	->Para igualar estado del repositorio local al de el remoto (bajar cambios) usa "git pull origin" o "git fetch" seguido de "git merge". 
	  NOTA: Es buena idea usar con frecuencia git fetch para sincronizar los datos del repositorio local con el de el remoto. 

IMPORTANTE:

	->Usar con frecuencia "git status", "git log" y "git remote show origin" pues dan mucha info de lo que está pasando.

	->Este enlace está to rico: https://git-scm.com/book/en/v2

	->Y este también: https://product.hubspot.com/blog/git-and-github-tutorial-for-beginners


PD: Perdón por el autismo. :3
