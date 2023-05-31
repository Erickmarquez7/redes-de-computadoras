# Equipo-AAR-ATDI-BME-DAAV-LMAM

| Integrante                     | Número de Cuenta | Usuario de GitLab   |
|:------------------------------:|:----------------:|:-------------------:|
| Acosta Arzate Rubén            | 317205776        | `rubenAcostaArzate` |
| Alvarado Torres David Ignacio  | 316167613        | `ddalt`             |
| Bernal Marquez Erick           | 317042522        | `Erickmarquez7`     |
| Deloya Andrade Ana Valeria     | 317277582        | `avdeloya13`        |
| López Miranda Angel Mauricio   | 317034808        | `MauricioLMiranda`  |


## Explicación del proceso de creación de las imagenes de contenedor

Antes de la creación nos aseguramos de que docker se haya instalado correctamente de la siguiente pagina https://www.docker.com/products/docker-desktop/ y probamos con el siguiente comando

```
usuario@laptop docker run -it hello-world
```
No debería mostrar error alguno

Una vez que nos hayamos asegurado de la correcta instalación iniciamos sessión con 

```
usuario@laptop~$ docker login docker.io
```

Nos pedirá usuario y contraseña

Para la creación hacemos un __dockerfile__ como se explica en el siguiente archivo

[dockerfile](files/linux-doc/Dockerfile)

La explicación viene en los comentarios del mismo archivo

Construimos la imagen con __docker build__.

```
usuario@laptop~$ TAG=[usuario]/[contenedor]
usuario@laptop~$ docker build --progress plain -t "${TAG}" ./
```

Utilizamos __--progress plain__ para capturar la salida de __docker build__

Verificamos listando las imagenes del contenedor con

```
docker images
```

Por ultimo enviamos las imagenes al __registry__

```
usuario@laptop~$ TAG=[usuario]/[contenedor]
usuario@laptop~$ docker push "${TAG}"
```


## Explicación del proceso de instalación de k3s en Debian 11

## Explicación del proceso de instalación del ingress controller en el cluster

## Explicación del proceso de despliegue de los sitios web en el cluster de Kubernetes

## Explicación de la configuración de SSL/TLS en el ingress controlle