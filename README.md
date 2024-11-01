# podman
Some examples with podman

Generar la imagen:

```podman build -t php-56-rhel7:1.0 .```

Listar las imagenes:

```podman image list```

Create online examination system pod: (from: https://projectworlds.in/free-projects/php-projects/online-examination/)

```podman pod create --name oes -p 8080:8080```

Bajar el programa php (from: https://shorturl.at/goASW )

Crear un contenedor para indicar donde se ubicaran las fuentes de php:

```podman run -d --read-only --restart unless-stopped --pod oes -v /home/juancvilla/projects/online-examination-systen-in-php-master/:/var/www/html/ --tmpfs /var/log --tmpfs /var/tmp --name myc php-56-rhel7:1.0```

Puedes detener el pod con el comando:

```podman pod stop oes```

Puedes verificar que efectivamente no este corriendo, con el comando:

```podman ps -a --pod```

Puedes volver a levantar el pod con el comando:

```podman pod start oes```

Crear un pod para la Base de datos:

```podman run -d --restart unless-stopped --pod oes --name myd -v /home/juancvilla/projects/online-examination-systen-in-php-master/mysql:/var/lib/mysql -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin -e MYSQL_DATABASE=project rhel8/mariadb-103```

Revisar que esten corriendo:

```podman ps -a --pod```

Si no esta corriendo ejecutar:

```podman pod start oes```

Para crear la base de datos y sus tablas por primera vez:

```podman exec -it myd bash```

Conectarse a la base de datos con clave: admin

```$ mysql -h 127.0.0.1 -u admin -p
$ use database project;```

Ejecutar todas las acciones que se encuentran en archivo project.sql

head  pr







