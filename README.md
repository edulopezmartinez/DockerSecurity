# dockerSecGraduates2018

Requisitos:

docker
docker-compose

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

2.1 Modifica el docker-compose y el html/index.html con tus datos

2.2 Arrancar imagen

```
  $> docker-compose up -d

```

Ir al navegador y comprobar que se ha levantado el servidor: http://localhost

Comprueba con la ip de tus compañeros qué han puesto: http://ip_de_tu_compañero

2.3 Obtener tag y sha de la imagen base

Pista: Comprueba el Dockerfile ``` docker inpect IMAGEN_BASE ```

2.4 ¿Cuál es la imagen base que usa el Dockerfile?

2.5 ¿Cuál es el identificador único de la imagen base?

2.6 ¿Cuál es la tag de la imagen base?

2.7 ¿Cuál es el repodigest? ¿Qué es el Repodigest?


2.8 ¿Cuántas vulnerabilidades tiene la imagen base? Has de encontrar cuál es la imagen oficial
equivalente a la imagen base (OJO con ID!). (https://anchore.io)

2.9 Modifica el Dockerfile para que descargue de la imagen oficial (Utiliza el repodigest)

2.10 Finaliza los contenedores

```
  $> docker-compose down

```

2.11 Subir mi imagen a mi dockerhub

```
  $> docker push USUARIO/yo:ej2

```

## Ej3: Buenas prácticas con Docker (20 min)

Preparación:


```
cd Ej3
sudo chown root:root -R top_secret
sudo chmod 400 -R top_secret
```

3.1 Docker bench for security

```
  $> docker-compose up -d

```

https://github.com/docker/docker-bench-security


```
docker run -it --net host --pid host --userns host --cap-add audit_control     -e DOCKER_CONTENT_TRUST=$DOCKER_CONTENT_TRUST     -v /var/lib:/var/lib     -v /var/run/docker.sock:/var/run/docker.sock     -v /usr/lib/systemd:/usr/lib/systemd     -v /etc:/etc --label docker_bench_security     docker/docker-bench-security
```

¿En qué punto aparece que no corras el usuario como root?

3.2 ¿Qué permisos tiene el directorio top_secret y password dentro del contenedor?
```
docker exec -it ej3_app_1 ls -la top_secret
dr-------- 2 root root 4096 Jun  6 14:35 .
drwxr-xr-x 1 root root 4096 Jun  6 14:43 ..
-r-------- 1 root root    9 Jun  6 14:41 password.html

```

¿Por qué es accesible si es una top_secret y tiene esos permisos?

```
http://localhost/top_secret
```

3.3 Crear usuario en el Dockerfile que arranque
```
  $> docker-compose down

```

```
RUN groupadd -g 999 appuser && \
    useradd -r -u 999 -g appuser appuser
USER appuser
```

```
  $> docker-compose up

```

```
http://localhost/top_secret
```

¿Qué ha ocurrido? ¿Es accesible ahora el directorio top_secret?

Limpia tus contenedores:

```
  $> docker-compose down

```

3.4 Subir mi imagen a mi dockerhub

```
  $> docker push USUARIO/yo:ej3

```

## Ej4. Limpieza de vulnerabilidades (20 min)

4.1 Adapta tu Dockerfile para que tu imagen no tenga vulnerabilidades.

Si es necesario puedes acceder al contenedor para probar cosas:

```
docker run --rm -it IMAGE bash
```

4.2 Subir mi imagen a mi dockerhub

```
  $> docker push USUARIO/yo:ej4

```


## Ej5. ¿Qué hacemos en Chimera? (20 min)

## Ej6. Bonus: Conseguir que mi imagen ocupe lo mínimo posible con todo lo que hemos visto anteriormente (20 min)


```
  $> docker push USUARIO/yo:ej5

```
