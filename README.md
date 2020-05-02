Descripcion comandos git
- Creacion de tag de commits usamos el ```git tag``` creamos una etiqueta para el commit en curso de esta manera en ves usar el SHA del commit etiquetamos y le ponemos una version a ese commit por ejemplo ```git tag "v1.0.0"```
- Para hacer un commit inmediato con add ```git add .``` y  ```git commit -m "mensaje"``` en un solo comando hacemos ```git commit -am "detalle del comit"```
- Crear una rama(si ya esta creada se mueve solamente) y moverse a ella en un solo paso: ```$ git checkout -b "homologacion"```

- Listar las ramas en local: ```$ git branch``` y si deseamos ver las ramas en remoto que estan alineadas en local: ```git branch -a```, ojo pero no nos listara todas, si en caso hubieran creado otras recientemente, para estar actualizado de las demas ramas existente ejecutamos el siguiente comando: ```$ git fetch origin```,  y si queremos que se saquen las referencias a las ramas que ya no existen ejecutamos ```$ git fetch -ap```

Alias de GIT
- Para mac por ejemplo podemos ejecutar ```$ vim $HOME/.gitconfig```, una vez abierto el archivo de configuración agregamos(de no tenerlo) las siguientes lineas ```[alias] st = status```, y lo podemos verificar revisando el .gitconfig con: ```$ cat $HOME/.gitconfig```

Alias de consola
- podemo crear un alias por ejemplo para el comando de ver el log de commits, por ejemplo ```$ alias gl="git log"```


## Buenas prácticas a la hora de hacer el ignore

- tenemos que manejar los ignore global, para ello creamos un archivo gitignore en el home de nuestro sistema operativo(no es una regla fija pero es una buena práctica), entonces lo haríamos así: ```touch $HOME/.gitignore_global``` 
- Lo siguiente es decirle a git que lo aplique como una regla de exclusión global ```git config --global core.excludesfile $home/.gitignore_global```

Igual que podemos establecer reglas de exclusión tanto a nivel global como a nivel de repositorio, en Git existen varios niveles para la configuración misma:

- ```git config --system``` Aplica a todos los repositorios de todos los usuarios del sistema y suele residir en /etc/gitconfig.
- ```git config --global``` Aplica a todos los repositorios del usuario actual y suele residir en ~/.gitconfig.
- ```git config --local``` Aplica únicamente al repositorio en el que estemos trabajando y suele residir en ./git/config dentro del proyecto. Es la opción predeterminada y por tanto se suele omitir.

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
- [] Admin
- [] header
