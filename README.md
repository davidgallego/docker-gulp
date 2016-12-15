Imagen basada en mhart/alpine-node:7 que además instala ruby y git

Para su configuración montamos el mismo volumen que para el servidor web y en el attributo working_dir ponemos el directorio donde tengamos nuestro gulpfile.js

Esta receta de docker crea en el _container_ un usuario con el mismo nombre y uid que el usuario local de nuestro equipo que está lanzando docker.

De esta forma, evitamos trabajar como _root_, con lo que los ficheros creados por docker serán propiedad de nuestro usuario local.

### Preparación del entorno (si ya se tiene instalado omitir)

* Instalar Docker  (https://docs.docker.com/engine/installation/) hay que ejecutar docker con nuestro usuario local para ello hay que asignar nuestro usuario al grupo "docker" para poder ejecutar docker sin sudo
```sh
sudo groupadd docker
sudo usermod -aG docker `whoami`
```
* Instalar docker-compose (https://docs.docker.com/compose/install/)

### Inicio (+info: alberto.silva@biko2.com)
Para que funcione, hay que definir un par de variables (mediante docker-set-enviroment.sh) antes de hacer el build de la imagen.
```sh
$ source docker-set-enviroment.sh
$ docker-compose build
$ docker-compose up
$ docker exec -it {nombre_contenedor} bundle install
$ docker exec -it {nombre_contenedor} npm install
```
Una vez hecho el build, podemos ejecutar gulp (o cualquier task):
```sh
 $ docker exec -it {nombre_contenedor} gulp
```
