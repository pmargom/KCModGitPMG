#MODULO GIT: Respuestas ejercicios prácticos.

**EJERCICIO 1**

A continuación, se listan las preguntas y respuestas correspondientes al ejercicio 1.

**Pregunta 11) Deshacer el último commit (perdiendo los cambios realizados en el working copy)**:

*¿Qué comando utilizaste en el paso 11?*

git reset --hard head~1

*¿Por qué?*

El comando que git nos ofrece para movernos entre acciones realizadas es "git reset". 
Con el cualificador "--hard" le indicamos que queremos eliminar los cambios del working copy.
La expresión "head~1" indica que queremos mover el puntero head al commit anterior al actual, lo que 
"deshará" la operación commit que se solicita en este punto del ejercicio.

**Pregunta 12) Rehacer el último commit (el que acabamos de deshacer)**:

*¿Qué comando o comandos utilizaste en el paso 12?*

git reset --hard d6ecaaf

*¿Por qué?*

El comando que git nos ofrece para movernos entre acciones realizadas es "git reset".
Con el cualificador "--hard" le indicamos que queremos eliminar los cambios del working copy.
El valor "d6ecaaf" identifica al commit al que queremos volver.

**Pregunta 13) Hacer un merge con ‘master’ (htmlify absorbe a master)**:

*El merge del paso 13, ¿Causó algún conflicto?*

No.

*¿Por qué?*

Cuando se crea la rama htmlify, el puntero head de master y htmlify apuntan al mismo nodo en el grafo.
Luego se modifica el fichero poem.md en la rama htmlify y al hacer commit, genera un nuevo nodo en el grafo.
En este punto, el grafo tiene 2 nodos, que si los llamaos A y B, tendríamos:

	.- master apunta a A
	.- htmlify apunta a B (y B es hijo de A).

Ambas ramas formarían una lista. La hacer le merge, la idea es que la rama que absorve, htmlify, tenga sus nodos
y "añada" (los haga accesibles) los de la rama absorvida, master. Pero es que este punto, ya la rama htmlify
tiene o puede acceder a los nodos de master.

**Pregunta 19) Hacer un merge de “matrix” en “htmlify” (htmlify absorbe a matrix)**:

*¿Causó algún conflicto?:* 

Sí. 

*¿Por qué?* 

Porque hemos cambiado el contenido del mismo fichero en dos ramas diferentes y git necesita aclarar
cuál será el contenido para el fichero al unir las dos ramas. Para ello, necesita crear un nuevo nodo en el 
que convergan ambas ramas, haciendo un merge "no fast forward". En el nuevo nodo para concretar el merge, es
dónde la versión final del fichero en conflicto debe ser considerado.

**Pregunta 21) Desde “master”, hacer un merge con “htmlify”**

*El merge del paso 21, ¿Causó algún conflicto?*

No.

*¿Por qué?*

Porque ahora master y htmlify forman una lista. Lo único que hay que hacer es mover el puntero head de la rama
master al mismo nodo en el grafo al que apunta el puntero head de htmlify. Esto se puede resolver con un merge
Fast-forward.

**Pregunta 25) Dibujar el diagrama**

git log --graph --decorate --pretty=oneline


**Pregunta 26) Hacer un merge “no fast-forward” de “title” en “master” (master absorbe a title)**

*El merge del paso 26, ¿Podría ser fast forward?*

Sí.

*¿Por qué?*

Si estando en la rama title, miramos el diagrama, tenemos lo siguiente:

* 5234e3f1fce66da3ec490ae215ca0bb1d9a75631 (HEAD, title) Ejercicio 1, punto 23. Añado un título al fichero
*   a47059e20b6b525bf8a935fc8eea0dc828fa0204 (master, htmlify) Resolución de comflictos ejercicio 1, punto 20
|\
| * c7276ec29e9b6f3c3973de6ba2616a82d4960697 (matrix) Modificación según el ejercicio 1, puntto 17
* | d6ecaaf08aada94714aaec93365f341f9ee0c3f9 Cambio los nombres de colores por sus valores hexadecimal
|/
* adff765d2d78573cccc355de661d19382ee8aa86 Inicio: Primer commit

Vemos que el último commit the master (pénultimo en el diagrama) y el último commit de title (último 
en el diagrama) forman una lista. En este caso, se podría haber realizado un merge fast-forward y hacer que 
el puntero head de master pasara a apuntar al commit al que apunta el puntero head de title. Al ser master quien
absorve a title, solo necesita poder "incluir" los nodos que le faltan de title.

Al forzar el merge no-fast-forward, obtenedremos un nuevo nodo en el que converjan ambas ramas. Esto se pude ver 
en el diagrama siguiente después de hecho el merge no-fast-forward:

*   ec1d0737c8f6a98ee0978672441894e5e5f03cb5 (HEAD, master) Merge branch 'title'
|\
| * 5234e3f1fce66da3ec490ae215ca0bb1d9a75631 (title) Ejercicio 1, punto 23. Añado un título al fichero
|/
*   a47059e20b6b525bf8a935fc8eea0dc828fa0204 (htmlify) Resolución de comflictos ejercicio 1, punto 20
|\
| * c7276ec29e9b6f3c3973de6ba2616a82d4960697 (matrix) Modificación según el ejercicio 1, puntto 17
* | d6ecaaf08aada94714aaec93365f341f9ee0c3f9 Cambio los nombres de colores por sus valores hexadecimal
|/
* adff765d2d78573cccc355de661d19382ee8aa86 Inicio: Primer commit

**Pregunta 27) Deshacer el merge (sin perder los cambios del working copy)**

	git reset 5234e3f (donde 5234e3f HEAD@{4}: commit: Ejercicio 1, punto 23. Añado un título al fichero)

**Pregunta 28) Descartar los cambios**

*¿Qué comando o comandos utilizaste en el paso 28?*

	git stash

**Pregunta 29) Eliminar la rama “title”**

	git branch -D title

**Pregunta 30) Rehacer el merge que hemos deshecho**

	git reset --hard 8cd3509 (8cd3509 HEAD@{1}: merge title: Merge made by the 'recursive' strategy)
 

**Pregunta 32) Volver al commit inicial cuando se creó el poema**

	git reset --hard adff765d2d78573cccc355de661d19382ee8aa86 

	(donde adff765d2d78573cccc355de661d19382ee8aa86 identifica al commit inicial)

**Pregunta 33) Volver al estado final, cuando pusimos título al poema**

	git reset --hard e4f547d 

	(donde e4f547d HEAD@{7}: commit: Ejercicio 1, punto 23. Añado un título al fichero)
