Docker OpenCart
========================

Contenedores e imagnes especializadas para cualquier proyecto symfony2, particularmente fue adaptado para OpenCart.

Este documento contiene toda la informacion necesaria para levantar los contenedores necesarios para obtener 
un entorno de desarrollo totalmente funcional. 

Especifiaciones
----------------------------------
docker-core
docker-compose
PHP 5.6.30
NGINX latest
MYSQL 5.7.16

Instalar contenedores
----------------------------------
Si todavia no se encuentra dentro de la carpeta docker:

	cd PROJECT_ROOT/docker

Crear la carpeta data/mysql que almacenara la informacion de las bases de datos

Ejecutar:

	docker-compose up --build

Acceder al contenedor php para instalar el proyecto (asegurarse no tener otro contenedor creado con el mismo nombre):

	docker exec -it 'opencart_php' bash

Proceder a la instalacion del proyecto Symfony2 normalmente dentro del contenedor.

Informacion adicional
----------------------------------
Sobre los directorios:

  * data: guarda las BD creadas en los contenedores de MYSQL.

  * php : configuracion del contenedor php

  * nginx: configuracion del contenedor de nginx (por ej.: virtual host en nginx.conf)

Informacion adicional:

  * En la carpeta /php los archivos .bashrc y .gitconfig son para editar estos archivos propios del contenedor sin necesidad de entrar a los mismos.

Comandos utiles
----------------------------------
docker-compose up [Lee archivo docker-compose.yml e incia los servicios configurados]
docker-compose build [Lee Archivo docker-compose.yml Y RECONFIGURA los servicios en caso de haber algun cambio].
docker ps [lista los contenedores iniciados]
docker ps -a [lista todos los contenedores]
docker stop 'nombre_or_id_container' [detiene un contenedor o varios]
docker stop $(docker ps -a -q) [detiene todos los contenedores que se estan ejecutando]
docker start 'nombre_or_id_container' [inicia un contenedor o varios]
docker restart 'nombre_or_id_container' [reinicia un contenedor o varios]
docker rm 'nombre_or_id_container' [Elimina un contenedor]
docker rm $(docker ps -a -q) [Elimina todos los contenedores]
docker rmi 'nombre_or_id_imagen' [Elimina una imagen]
docker rmi $(docker images -q) [Elimina todas las imagenes]
docker exec -it 'nombre_or_id_container' bash [entras al contenedor]
docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container_name_or_id" [Muestra IP de un contenedor]
ping nombre_or_id_container [cmando dentro de algun contendor para saber la ip de este].