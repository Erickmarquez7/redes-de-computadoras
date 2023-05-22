# Equipo-AAR-ATDI-BME-DAAV-LMAM

| Integrante                     | Número de Cuenta | Usuario de GitLab   |
|:------------------------------:|:----------------:|:-------------------:|
| Acosta Arzate Rubén            | 317205776        | `rubenAcostaArzate` |
| Alvarado Torres David Ignacio  | 316167613        | `ddalt`             |
| Bernal Marquez Erick           | 317042522        | `Erickmarquez7`     |
| Deloya Andrade Ana Valeria     | 317277582        | `avdeloya13`        |
| López Miranda Angel Mauricio   | 317034808        | `MauricioLMiranda`  |

# [Examen 3](https://redes-ciencias-unam.gitlab.io/2023-2/laboratorio/examen-3/)


## Explicación breve de la instalación del stack web en la máquina virtual de la nube

### Registros DNS

En nuestros servicios de nube buscamos las que diga _zonas DNS_, en nuestro caso Microsoft Azure, una vez estando ahí deramos click al botón que nos permita agregar la zona DNS, nos pedirá el nombre, tipo y diferentes valores de acuerdo al tipo.

![](img/DNS.jpeg)

### VirtualHost de Apache HTTPD

(aki Vale)

Para revisar los archivos habilitados de VirtualHosts

```
root@example:~# ls -la /etc/apache2/sites-enabled
```

Para revisar la ruta de la raíz del sitio web en los VirtualHost

```
root@example:~# grep 'DocumentRoot' /etc/apache2/sites-enabled/*.conf
```
### Instalación y configuración de PHP

(esta parte david pk el lo hizo xd)

### Instalación y configuración de MySQL/MariaDB

(esta parte david pk el lo hizo xd)


## Explicación detallada de cómo se implementaron las características adicionales en la instalación de WordPress.

### Multi-sitio 

(aki Vale)

### Autenticación digest para wp-admin

### Correo AWS SES

## Archivos adjuntos

En esta ocasión los archivos adjuntos se enviarán a través de Google Drive por medio de una carpeta compartida.