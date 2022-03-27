---
title: Ejercicios 2 docker
author: Neri Sánchez González - Pola
---

# Resolución del ejercicio 2 - almacenamiento
---

> Realizado por Neri Sánchez

### Bind mount para compartir datos

Mediante comandos creamos una carpeta llamada **saludo** y dentro de ella creamos un fichero llamado `index.html` con el siguiente contenido: `<h1>HOLA SOY Neri</h1>`

```
mkdir saludo
cd saludo
echo "<h1>HOLA SOY Neri</h1>" > index.html
cat index.html
```

<img src="Ejercicio2.assets\1.png" style="zoom:67%;" />

------

Una vez hecho esto arrancar dos contenedores basados en la imagen **php:7.4-apache** que hagan un bind mount de la carpeta `saludo` en la carpeta `/var/www/html` del contenedor. Uno de ellos vamos a acceder con el puerto 8181 y el otro con el 8282. Y su nombres serán `c1` y `c2` .

```
sudo docker run -d --name c1 -v /home/nerisg/saludo:/var/www/html -p 8181:80 php:7.4-apache
```

> Pantallazo con la orden correspondiente para arrancar el contenedor c1 (puerto 8181) realizando el bind mount solicitado.

<img src="Ejercicio2.assets\2.png" />

```
docker run -d --name c2 -v /home/nerisg/saludo:/var/www/html -p 8282:80 php:7.4-apache
```

> Pantallazo con la orden correspondiente para arrancar el contenedor c2 (puerto 8282) realizando el bind mount solicitado.

<img src="Ejercicio2.assets\3.png" />

> Pantallazo con los dos contendedores creados

<img src="Ejercicio2.assets\4.png" />

> Pantallazo donde se pueda apreciar que accediendo a c1 se puede ver el contenido de index.html . 

<img src="Ejercicio2.assets\5.png" />

> Pantallazo donde se pueda apreciar que accediendo a c2 se puede ver el contenido de index.html . 

<img src="Ejercicio2.assets\6.png" />

------

Modificamos el archivo `index.html`

```
cd saludo
echo "<h1>HOLA SOY Neri</h1>" > index.html
cat index.html
```

<img src="Ejercicio2.assets\7.png" />

> Otros dos pantallazos donde se vea el acceso al fichero index.html después de modificarlo. 

<img src="Ejercicio2.assets\8.png" style="zoom:67%;" />

<img src="Ejercicio2.assets\9.png" style="zoom:67%;" />

------

> Borrar los dos contenedores. Mostrar que se han borrado.

```
cd docker ps -a -s
sudo docker stop <contenedor>
sudo docker rm <contenedor>
```

<img src="Ejercicio2.assets\10.png" />

