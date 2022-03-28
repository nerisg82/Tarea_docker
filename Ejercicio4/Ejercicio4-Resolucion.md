---
title: Ejercicios 4 docker
author: Neri Sánchez González - Pola
---

# Resolución del ejercicio 4 - imagen con Dockerfile
---

> Realizado por Neri Sánchez

> Pantallazo/bloque de código con el Dockerfile

<img src="Ejercicio4.assets\7.png" style="zoom:67%;" />

<img src="Ejercicio4.assets\2.png"/>

> Pantallazo donde se vea el comando que crea la nueva imagen.

```
docker build -t servidor_nerisg .
```

<img src="Ejercicio4.assets\8.png"/>

------

> Pantallazo donde se ve el acceso al navegador con el sitio servido

```
docker run --name servidor_nerisg -d -p 80:80 servidor_nerisg:latest
```

<img src="Ejercicio4.assets\3.png"/>

<img src="Ejercicio4.assets\5.png" style="zoom:67%;" />

------

Subimos la imagen a nuestro Docker Hub

```
docker tag servidor_nerisg:latest nerisg/servidornerisg:latest
docker push nerisg/servidornerisg:latest
```

<img src="Ejercicio4.assets\6.png"/>

> Pantallazo donde se vea la imagen subida a tu cuenta de Docker Hub

<img src="Ejercicio4.assets\4.png" style="zoom:67%;" />

