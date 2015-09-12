1) Crear un repositorio:

	1.1.- Creo la carpeta en la que se almacenarán los ficheros del repo y me muevo a ella: 
		mkdir KCModGitPMG
		cd KCModGitPMG
	1.2.- git init

2) Crear un archivo “poem.md”:

	nano poem.md (y añado el contenido)

3) Añadir poem.md al staging area:

	git add poem.md

4) Mover lo que hay en el staging area al repositorio:

	git commit -m "Inicio: Primer commit"


5) Crear una rama llamada “htmlify”:

	git branch htmlify

6) Listar las ramas que hay en el repositorio:

	git branch

7) Moverse a la rama “htmlify”:

	git checkout htmlify

8) Comprobar que se está en la rama correcta:

	git branch

9) Modificar en el archivo poem.md:

	nano poem.md (modifico el contenido y guardo los cambios)

10) Añadir los cambios al staging área y luego pasarlos al repositorio:

	10.1.- Añadir los cambios al stagging área:

		git add poem.md

	10.2.- Pasar los cambios al repositorio:

		git commit -m "Cambio los nombres de colores por sus valores hexadecimal"

11) Deshacer el último commit (perdiendo los cambios realizados en el working copy):

	git reset --hard head~1

12) Rehacer el último commit (el que acabamos de deshacer):

	12.1- Primero consulto el reflog para ver los movimientos:

		git reflog

	12.2.- Me desplazo al commit en el que se guardaron los cambios de colores a valores hexadecimal:

		git reset --hard d6ecaaf (donde: d6ecaaf HEAD@{5}: commit: Cambio los nombres de colores por sus valores hexadecimal)

13) Hacer un merge con ‘master’ (htmlify absorbe a master):

	git merge master

14) Volver a la rama master:

	git checkout master

15) Crear una nueva rama llamada “matrix”:

	git branch matrix

16) Entrar en matrix (cambiar a la rama matrix):

	git checkout matrix

17) Modificar en el archivo poem.md: 

	nano poem.md (y añado las modificaciones indicadas en el enunciado)

18) Hacer un commit:

	18.1.- Añado el fichero al stagging área:

		git add poem.md

	18.2.- Hago el commit:

		git commit -m "Modificación según el ejercicio 1, puntto 17"

19) Hacer un merge de “matrix” en “htmlify” (htmlify absorbe a matrix):

	19.1.- Me cambio a la rama htmlify:
		
		git checkout htmlify

	19.2.- Hago el merge:

		git merge matrix

20) Si hay conflictos, deberemos resolverlos quedándonos con el contenido de la rama “htmlify”:

	En el paso anterior, se producen conflictos al hacer el merge de ramas. Para resolverlo, editamos el fichero 
	poem.md para ver los conflictos. El contenido es el siguiente:

<<<<<<< HEAD
Roses are #ff0000,

Violets are #0000ff.
=======
Red pills are red,

Blue pills are blue.
>>>>>>> matrix

All of my base

Como en el punto indica que, en caso de conflicto, debemos quedarnos con el contenido de la rama htmlify, editamos el fichero
quedando como se muestra a continuación:

Roses are #ff0000,

Violets are #0000ff.

All of my base

are belong to you.

Por último, hay que hacer efectiva la resolución del conflicto, añadiendo el fichero al staggin área y haciendo el posterior commit:

git add poem.md
git commit -m "Resolución de comflictos ejercicio 1, punto 20"

21) Desde “master”, hacer un merge con “htmlify”:

	21.1.- Me muevo a la rama master

	git checkout master

	21.2.- Hago el merge con la rama htmlify:

	git merge htmlify

	
22) Crear una rama “title” y cambiarse a esa rama:

	22.1.- Creo la rama:

		git branch title

	22.2.- Me cambio a ella:

		git checkout title

23) Añadir un título (a tu gusto) al archivo poem.md y hacer un commit:

	23.1.- Edito el fichero y añado el título:

		nano poem.md

	23.2.- Hago el commit:

		git add poem.md
		git commit -m "Ejercicio 1, punto 23. Añado un título al fichero"		

24) Volver a la rama master:

	git checkout master

25) Dibujar el diagrama:

	git log --graph --decorate --pretty=oneline

27) Deshacer el merge (sin perder los cambios del working copy):

	git reset 5234e3f (donde 5234e3f HEAD@{4}: commit: Ejercicio 1, punto 23. Añado un título al fichero)

28) Descartar los cambios:

	git stash

29) Eliminar la rama “title”:

	git branch -D title


30) Rehacer el merge que hemos deshecho:

	git reset --hard 8cd3509 (8cd3509 HEAD@{1}: merge title: Merge made by the 'recursive' strategy)

31) Volver a master y eliminar el resto de ramas:

	31.1.- Volver a master:

		git checkout master
	
	31.2.- Eliminar el resto de ramas:
	
		git branch -D htmlify
		git branch -D matrix

32) Volver al commit inicial cuando se creó el poema:

        git reset --hard adff765d2d78573cccc355de661d19382ee8aa86

        (donde adff765d2d78573cccc355de661d19382ee8aa86 identifica al commit inicial)
	
33) Volver al estado final, cuando pusimos título al poema:

        git reset --hard e4f547d

        (donde e4f547d HEAD@{7}: commit: Ejercicio 1, punto 23. Añado un título al fichero)

	
34) Crear los siguientes tags: 

	En general, primero hay que posicionarse en el commit a etiquetar (git reset --hard <identificador del commit>).
	Luego crear el tag con el comando:

		git tag <tag_name>

35) Ir al tag matrix:

	git reset matrix







