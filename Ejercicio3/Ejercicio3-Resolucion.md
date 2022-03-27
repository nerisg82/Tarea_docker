---
title: Ejercicios 3 docker
author: Neri Sánchez González - Pola
---

# Resolución del ejercicio 3 - redes
---

> Realizado por Neri Sánchez

En primer lugar creamos una red bridge con el nombre redbd:

```
docker network create redbd
```

<img src="Ejercicio3.assets\0.png" style="zoom:67%;" />

Al tener descargada la imagen MariaDB de tareas anteriores solo tenemos que crear el contenedor:

```
docker run --name bbddredes --network redbd -v /home/docker/datadir:/var/lib/mysql -e MARIADB_ROOT_PASSWORD=root -p 3306:3306 -d mariadb
```

<img src="Ejercicio3.assets\2.png"/>

------

Para poder conectarnos a la base de datos, tras crear el contenedor ahora hay que usar el de Adminer para que se conecte a la base de datos:

```
docker run --name adminer --network redbd --link bbddredes:mariadb -p 8080:8080 -d adminer
```

<img src="Ejercicio3.assets\1.png" style="zoom:67%;" />

------

> Pantallazos donde se vean los contenedores creados y en ejecución 

<img src="Ejercicio3.assets\3.png" style="zoom:67%;" />

------

> Pantallazo donde se vea el acceso a la BD a través de la interfaz web de Adminer 

<img src="Ejercicio3.assets\4.png" style="zoom:67%;" />

> Pantallazo donde se vea la creación de una BD con la interfaz web Adminer 

<img src="Ejercicio3.assets\5.png" style="zoom:67%;" />

<img src="Ejercicio3.assets\6.png" style="zoom:67%;" />

> Pantallazo donde se entre a la consola del servidor web en modo texto y se compruebe que se ha creado la BD 

```
mysql -u root -p
show databases;
```

<img src="Ejercicio3.assets\7.png" style="zoom:67%;" />



------

Mostramos todos los volúmenes y contenedores:

```
sudo docker volume ls
sudo docker ps -a -s
```

<img src="Ejercicio3.assets\8.png" style="zoom:67%;" />

Paramos y borramos los contenedores con los comando `stop` y `rm`:

<img src="Ejercicio3.assets\9.png" style="zoom:67%;" />

Borramos todos los volúmenes

```
sudo docker volume prune
```

<img src="Ejercicio3.assets\11.png" style="zoom:67%;" />

Comprobamos que se han borrado los contenedores, la red, y los volúmenes utilizados

```
sudo docker volume ls
sudo docker ps -a -s
```

<img src="Ejercicio3.assets\12.png" style="zoom:67%;" />

