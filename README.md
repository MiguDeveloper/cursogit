Descripcion comandos git
- Creacion de tag de commits usamos el ```git tag``` creamos una etiqueta para el commit en curso de esta manera en ves usar el SHA del commit etiquetamos y le ponemos una version a ese commit por ejemplo ```git tag "v1.0.0"```
- Para hacer un commit inmediato con add ```git add .``` y  ```git commit -m "mensaje"``` en un solo comando hacemos ```git commit -am "detalle del comit"```
- Crear una rama(si ya esta creada se mueve solamente) y moverse a ella en un solo paso: ```$ git checkout -b "homologacion"```

- Listar las ramas en local: ```$ git branch``` y si deseamos ver las ramas en remoto que estan alineadas en local: ```git branch -a```, ojo pero no nos listara todas, si en caso hubieran creado otras recientemente, para estar actualizado de las demas ramas existente ejecutamos el siguiente comando: ```$ git fetch origin```,  y si queremos que se saquen las referencias a las ramas que ya no existen ejecutamos ```$ git fetch -ap```

Alias de GIT
- Para mac por ejemplo podemos ejecutar ```$ vim $HOME/.gitconfig```, una vez abierto el archivo de configuración agregamos(de no tenerlo) las siguientes lineas ```[alias] st = status```, y lo podemos verificar revisando el .gitconfig con: ```$ cat $HOME/.gitconfig```

Alias de consola
- podemo crear un alias por ejemplo para el comando de ver el log de commits, por ejemplo ```$ alias gl="git log"```
