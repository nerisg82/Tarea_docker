title: Actividad Evaluable 3, GIT Y DOCKER
Primer Cuatrimestre - DAW - CIFP Sect. Industrial y de Servicios

author: Neri Sánchez González - Pola

## Actividad evaluable 3 - Git y Docker 

> ### AUTORA: NERI SÁNCHEZ GONZÁLEZ - POLA
>
> ###### DAW Distancia - CIFP Sect. Industrial y Servicios - La Laboral

[TOC]

### Ejercicio 1 - trabajo con imágenes

___

> ##### Servidor web

- Arranca un contenedor que ejecute una instancia de la imagen `php:7.4-apache` , que se llame `web` y que sea accesible desde un navegador en el puerto **8000**.
- Colocar en el directorio raíz del servicio web ( `/var/www/html` ) de dicho contenedor un fichero llamado `index.html` con el siguiente contenido:

```
<h1>HOLA SOY XXXXXXXXXXXXXXX</h1>
```

Deberás sustituir XXXXXXXXXXX por tu nombre y tus apellidos.

- Colocar en ese mismo directorio raíz un archivo llamado `mes.php` que muestre el nombre del mes actual. Ver la salida del script en el navegador 
- Borrar el contenedor

> **Servidor de base de datos**

- Arrancar un contenedor que se llame `bbdd` y que ejecute una instancia de la imagen **mariadb** 
- Antes de arrancarlo, visita la página en [Docker Hub]([Mariadb - Official Image | Docker Hub](https://hub.docker.com/_/mariadb))
- Establece las variables de entorno necesarias para que: 
  - La contraseña de root sea `root` . 
  - Crear una base de datos automáticamente al arrancar que se llame `prueba` .
  - Crear el usuario `invitado` con la contraseña `invitado` .

> **Entregar**

Un documento con los siguientes pantallazos, y los comandos empleados para resolver cada apartado: 

- Pantallazo que desde el <u>navegador</u> muestre el fichero `index.html` . 
- Pantallazo que desde un navegador muestre la salida del script `mes.php` . 
- Pantallazo donde se vea el tamaño del contenedor `web` después de crear los dos ficheros.
- Pantallazo de la consola de la Base de Datos donde se pueda observar que hemos podido conectarnos al servidor de base de datos con el usuario creado y que se ha creado la base de datos prueba ( `show databases` ). 
- Pantallazo donde se comprueba que no se puede borrar la imagen `mariadb` mientras el contenedor `bbdd` está creado. 
- Pantallazo donde se vean las imágenes que tienes en tu registro local. 
- Pantallazo donde se vea cómo se eliminan los contenedores utilizados.
