---
title: Ejercicios 1 docker
author: Neri Sánchez González - Pola
---

# Resolución del ejercicio 1 - trabajo con imágenes
---

> Realizado por Neri Sánchez

## Servidor web

En primer lugar conseguimos la imagen requerida: `php:7.4-apache`:

```
docker pull php:7.4-apache
```

<img src="Ejercicio1.assets\1.png" style="zoom: 50%;" />

Una vez lista crearemos el contenedor que correrá esta imagen:

```
sudo docker run -d --name web -p 8000:80 php:7.4-apache
```

<img src="Ejercicio1.assets\2.png"/>

------

Accedemos dinámicamente a Apache para colocar el archivo `index.html` y editarlo (una vez iniciamos la consola nos coloca en la carp /var/www/html)

```
docker exec -it web bash 
apt-get update
apt-get install nano
nano index.html
```

Insertamos la línea de código en el index.html y guardamos

<img src="Ejercicio1.assets\3.png"/>

> Pantallazo que desde el <u>navegador</u> muestre el fichero `index.html` . 

<img src="Ejercicio1.assets\4.png"/>

------

A continuación creamos el script PHP que mostrará el mes actual.

<img src="Ejercicio1.assets\5.png"/> 

> Pantallazo que desde un navegador muestre la salida del script `mes.php` . 

<img src="Ejercicio1.assets\6.png"/>

------

Después de añadir los archivos comprobamos el tamaño del contenedor:

```
sudo docker ps -a -s
```

> Pantallazo donde se vea el tamaño del contenedor `web` después de crear los dos ficheros.

<img src="Ejercicio1.assets\7.png"/>

------

Por último borramos el contenedor

```
docker stop 7c
docker rm 7c
```

<img src="Ejercicio1.assets\8.png"/>

------

## Servidor de base de datos

Descargamos una imagen de `mariadb`

```
sudo docker pull mariadb
```

<img src="Ejercicio1.assets\9.png"/>

A continuación creamos la base de datos:

```
docker run --name bbdd -e MARIADB_ROOT_PASSWORD=root -e MARIADB_DATABASE=prueba -e MARIADB_USER=invitado -e MARIADB_PASSWORD=invitado -p 3336:3306 -d mariadb
```

<img src="Ejercicio1.assets\10.png" />

Para hacer las pruebas es necesario crear el contenedor de phpMyAdmin añadiendo el 'flag' `--link`:

```
sudo docker pull phpmyadmin
sudo docker run --name myadmin -d -e PMA_ARBITRARY=1 --link bbdd:mariadb -p 8080:80 phpmyadmin

```

<img src="Ejercicio1.assets\11.png"/>

> Pantallazo de la consola de la Base de Datos donde se pueda observar que hemos podido conectarnos al servidor de base de datos con el usuario creado y que se ha creado la base de datos prueba ( `show databases` ). 

<img src="Ejercicio1.assets\12.png" />

<img src="Ejercicio1.assets\13.png"/>

------

Intentamos borrar la imagen mariadb:

```
sudo docker rmi mariadb
```

> Pantallazo donde se comprueba que no se puede borrar la imagen `mariadb` mientras el contenedor `bbdd` está creado. 

<img src="Ejercicio1.assets\14.png" />

------

> Pantallazo donde se vean las imágenes que tienes en tu registro local. 

```
sudo docker images
```

<img src="Ejercicio1.assets\15.png" style="zoom:67%;" />

------

> Pantallazo donde se vea cómo se eliminan los contenedores utilizados.

Listamos los contenedores

```
sudo docker ps -a -s
```

Borramos los usados durante la tarea

```
sudo docker rm e1
sudo docker rm 02
```

<img src="Ejercicio1.assets\16.png"/>

