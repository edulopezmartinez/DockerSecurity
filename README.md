# dockerSecGraduates2018

## Ej1: Dockerhub (5 min)

Crearse una cuenta en dockerhub: https://hub.docker.com/

En el terminal de tu ordenador, hacer login en dockerhub:

```
  $> docker login

Username: paquito
Password:
Login Succeeded

```

## Ej2: Identificar imagen base y análisis de vulnerabilidades de la misma (15 min)

2.1. Modifica el docker-compose y el html/index.html con tus datos

2.1. Arrancar imagen

```
  $> docker-compose up -d

```

Ir al navegador y comprobar que se ha levantado el servidor: http://localhost

Comprueba con la ip de tus compañeros qué han puesto: http://ip_de_tu_compañero

2.2. Obtener tag y sha de la imagen base

Pista: Comprueba el Dockerfile ``` docker inpect IMAGEN_BASE ```

2.2.1. ¿Cuál es la imagen base que usa el Dockerfile?

2.2.2. ¿Cuál es el identificador único de la imagen base?

2.2.3. ¿Cuál es la tag de la imagen base?

2.2.4. ¿Cuál es el repodigest? ¿Qué es el Repodigest?


2.2.4. ¿Cuántas vulnerabilidades tiene la imagen base? Has de encontrar cuál es la imagen oficial
equivalente a la imagen base (OJO con ID!). (https://anchore.io)

2.2.5. Modifica el Dockerfile para que descargue de la imagen oficial (Utiliza el repodigest)


## Ej3: Buenas prácticas con Docker

3.1 Crear un usuario que no sea root

3.1.1. ¿Qué permisos tiene password dentro del contenedor?
```
docker exec -it ej3_nginx_1 ls -la /usr/share/nginx/html/password
docker exec -it ej3_nginx_1 cat /usr/share/nginx/html/password
```

3.1.2.

3.2
