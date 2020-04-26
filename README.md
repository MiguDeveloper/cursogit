descripcion comandos git
- git tag : creamos una etiqueta para el commit en curso de esta manera en ves usar el SHA del commit etiquetamos y le ponemos una version a ese commit
- *git commit -am "detalle del comit"* => nos permite hacer dos cosas en una, el *git add .* y el *git commit -m "mensaje"*

- crear una rama(si ya esta creada se mueve solamente) y moverse a elle en un solo paso: *$ git checkout -b "homologacion"*

- listar las ramas en local: *$ git branch* y si deseamos ver las ramas en remoto: *git branch -a*, ojo pero no nos listara todas si en caso hubieran creado otras recientemente para estar actualizado ejecutamos el siguiente comando: *$ git fetch origin*,  y si queremos que se saquen las referencias a las ramas que ya no existen ejecutamos *$ git fetch -ap*

Este es un cambio ingresado desde github
