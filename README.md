# podman
Some examples with podman

Generar la imagen:

```podman build -t php-56-rhel7:1.0 .```

Listar las imagenes:

```podman image list```

Create image gallery pod: (from: [https://projectworlds.in](https://projectworlds.in/free-projects/php-projects/simple-image-gallery-in-php-with-source-code))

```podman pod create --name image-gallery -p 8080:8080```

Bajar el programa php (from: [https://projectworlds.in/wp-content/uploads/2019/06/image-gallery.zip](https://projectworlds.in/wp-content/uploads/2019/06/image-gallery.zip))

Crear un contenedor para indicar donde se ubicaran las fuentes de php:

```podman run -d --read-only --restart unless-stopped --pod image-gallery -v /home/juancvilla/projects/lamp1/:/var/www/html/ --tmpfs /var/log --tmpfs /var/tmp --name mydevcontainer php-56-rhel7:1.0```

Puedes detener el pod con el comando:

```podman pod stop image-gallery```

Puedes verificar que efectivamente no este corriendo, con el comando:

```podman ps -a --pod```

Puedes volver a levantar el pod con el comando:

```podman pod start image-gallery```







