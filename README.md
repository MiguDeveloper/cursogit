Descripcion comandos git

- Creacion de tag de commits usamos el `git tag` creamos una etiqueta para el commit en curso de esta manera en ves usar el SHA del commit etiquetamos y le ponemos una version a ese commit por ejemplo `git tag "v1.0.0"` y si deseas ver el tag creado ejecutamos `git tag` y si queremos subir el tag ejecutamos `git push --tag`
- Para hacer un commit inmediato con add `git add .` y `git commit -m "mensaje"` en un solo comando hacemos `git commit -am "detalle del comit"` recordemos que si tenemos un untracked no lo agregara solo los que tenemos en el working tree, para agregar los untracked debemos de usar primero el `git add .`
- Crear una rama(si ya esta creada se mueve solamente) y moverse a ella en un solo paso: `$ git checkout -b "homologacion"`

- Creacion de tag de commits usamos el `git tag` creamos una etiqueta para el commit en curso de esta manera en ves usar el SHA del commit etiquetamos y le ponemos una version a ese commit por ejemplo `git tag "v1.0.0"`
- Para hacer un commit inmediato con add `git add .` y `git commit -m "mensaje"` en un solo comando hacemos `git commit -am "detalle del comit"` recordemos que si tenemos un untracked no lo agregara solo los que tenemos en el working tree, para agregar los untracked debemos de usar primero el `git add .`
- Crear una rama(si ya esta creada se mueve solamente) y moverse a ella en un solo paso: `$ git checkout -b "homologacion"`

- Listar las ramas en local: `$ git branch` y si deseamos ver las ramas en remoto que estan alineadas en local: `git branch -a`, ojo pero no nos listara todas, si en caso hubieran creado otras recientemente, para estar actualizado de las demas ramas existente ejecutamos el siguiente comando: `$ git fetch origin`, y si queremos que se saquen las referencias a las ramas que ya no existen ejecutamos `$ git fetch -ap`

- Si queremos renombrar el ultimo commit ejecutamos `git commit --amend -m "modificacion del mensaje"`

- Regresar al último commit `git checkout -- .`

Alias de GIT

- Para mac por ejemplo podemos ejecutar `$ vim $HOME/.gitconfig`, una vez abierto el archivo de configuración agregamos(de no tenerlo) las siguientes lineas `[alias] st = status`, y lo podemos verificar revisando el .gitconfig con: `$ cat $HOME/.gitconfig`

Alias de consola

- podemo crear un alias por ejemplo para el comando de ver el log de commits, por ejemplo `$ alias gl="git log"`

## Buenas prácticas a la hora de hacer el ignore

- tenemos que manejar los ignore global, para ello creamos un archivo gitignore en el home de nuestro sistema operativo(no es una regla fija pero es una buena práctica), entonces lo haríamos así: `touch $HOME/.gitignore_global`
- Lo siguiente es decirle a git que lo aplique como una regla de exclusión global `git config --global core.excludesfile $home/.gitignore_global`

Igual que podemos establecer reglas de exclusión tanto a nivel global como a nivel de repositorio, en Git existen varios niveles para la configuración misma:

- `git config --system` Aplica a todos los repositorios de todos los usuarios del sistema y suele residir en /etc/gitconfig.
- `git config --global` Aplica a todos los repositorios del usuario actual y suele residir en ~/.gitconfig.
- `git config --local` Aplica únicamente al repositorio en el que estemos trabajando y suele residir en ./git/config dentro del proyecto. Es la opción predeterminada y por tanto se suele omitir.

- Cabe destacar que las propiedades de configuración se aplican en cascada desde el nivel de sistema hasta el local. De esta forma un valor de configuración establecido a nivel de sistema (--system) puede ser sobrescrito por cada proyecto en su ./git/config según las necesidades y convenciones de cada equipo.

- Por último la orden git config -l sirve para listar todos los valores de configuración del proyecto actual como resultado de fusionar los distintos niveles o ficheros de nuestro sistema. Para los que han trabajado con Maven alguna vez es como visualizar el POM efectivo.

## Buenas descripciones de commits

- Separa el título del contenido con un intro
- El título del commit no puede ser mas largo de 50 caracteres
- El cuerpo del commit no más de los 72 caracteres por linea
- Primera letra en mayúscula
- No acabes el commit con un punto
- Utiliza el modo imperativo al escribir
- Utiliza el cuerpo para explicar el 'que' y el 'por qué" del commit

## Tips para unas buenas descripciones de Pull/Merge Request

- El titulo del PR no ha de pasar los 72 carácteres
- Si la PR toca algo de la UI añadir un screenshot
- Si es algo de código muy complejo añadir algún grafico(UML)

## Estrategias de integración entre ramas

- para poder apreciar la graficamente los commits e integraciones podemos usar el comando `git log --graph --abbrev-commit --online`

git log

- `git log --oneline` nos permite mostrar los commit en una linea todos y no mostrar mucho detalle.

- Cualquier herramienta es más visualmente atractiva que el `git log` de consola. Aún así creo que merece la pena aprender un par de cosas sobre cómo usarla y especialmente los rangos de commits:

- `git log master feature-with-merge`. Muestra el histórico conjunto de todas las ramas (y commits) que le indiquemos. `Git log` sin argumentos muestra únicamente HEAD (la rama actual).

- `git log --all`. Un atajo para visualizar todas las ramas del repositorio.

- `git log master..feature-with-merge`. Muestra todos los commits que tiene la rama feature-with-merge que NO tiene master. Útil para revisar el trabajo que se ha hecho exclusivamente durante una feature o un bugfix.

- `git log feature-with-merge..master`. Lo mismo que el anterior pero al revés, lógicamente. Útil cuando quieres saber cómo de desactualizado estás con la rama con la que te vas a integrar.

- Particularmente encuentro difícil recordar en qué lado del rango tengo que poner cada rama (¿los nuevos commits son los de la derecha o los de la izquierda?). Por eso es útil esta última posibilidad:

  - `git log master...feature-with-merge` (nótense los 3 puntos y no 2). Muestra únicamente los commits que tienen distintos ambas ramas respecto de cada una. Equivale a:

  - `git log master..feature-with-merge && git log feature-with-merge..master`

- la suelo usar con un flag para marcar de dónde viene cada commit:

  - `git log --left-right master...feature-with-merge`. Te marca los commits exclusivos del lado derecho (feature-with-merge) con > y los del lado izquierdo con <.

Git Revert

- Para los casos en que hallamos ingresado un bug a master podemos ejecutar el comando `git revert @`

- Si queremos deshacer el ultimo commit podemos aplicar el comando ```git undo````

- Si por ejemplo se ha eliminado un archivo en master y hacemos un merge con nuestra rama local podemos descartar esos cambios con: git discard

- Si queremos ingresar unos cambios en el ultimo commit podemos usar: `git commit --amend`

- Usamos `git show hash_del_commit` y podemos ver los detalles del commit

- `git reset --mixed` Otra opción que encuentro interesante de git reset es el flag --mixed. Este te aborta el reset si ve que alguno de los ficheros que se van a "deshacer" está modificado en nuestra copia local, de forma que no perdamos cambios accidentalmente.

## Detectando cuando se metio un bug en nuestro codigo usando git

- Para ello nos apoyamos en el comando `git bisect start sha_commitfinal sha_commitinicio` detectado el commit lo marcamos como bueno con `git bisect good`

- para salir del bisect ejecutamos el comando `git bisect reset`
