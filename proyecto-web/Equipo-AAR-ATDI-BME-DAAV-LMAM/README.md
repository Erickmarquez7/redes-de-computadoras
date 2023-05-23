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

Para poder hacer la creación del VirtualHost redireccionamos http a https en el archivo proyecto.conf

Mientras que el el archivo aplicacion.conf se realiza la configuración de https, para el puerto ponemos el nombre del servidor y el alias. Además de agregar DocumentRoot y Directory ya que éstos se encuentran fuera de la carpeta var-www

### Instalación y configuración de PHP

(esta parte david pk el lo hizo xd)

### Instalación y configuración de MySQL/MariaDB

(esta parte david pk el lo hizo xd)


## Explicación detallada de cómo se implementaron las características adicionales en la instalación de WordPress.

### Multi-sitio 

Definimos el multisitio en el archivo wp-config.php agregando:  
/* Multisite */
define( 'WP_ALLOW_MULTISITE', true ); 

Esto para poder habilitar el menú de configuración de red. Luego nos vamos a donde dice: Administración > Herramientas > Configuración de red 

Después tenemos la opción de elegir entre subdominios y subdirectorios, en nuestro caso utilizamos subdirectorios. Verificamos los detalles de la red y presionamos el botón Instalar.

Ahora habilitaremos la red siguiendo los pasos que muestra la imagen a continuación: 

![](img/multisitios1.jpg)

Una vez hecho esto, iniciamos sesión nuevamente utilizando dando click en el enlace que nos proporcionan. 

Y ahora nos aparece "mis sitios" en la parte superior izquierda: 

![](img/multisitios2.jpg)

![](img/multisitios3.jpeg)

### Autenticación digest para wp-admin

### Correo AWS SES

## Archivos adjuntos

En esta ocasión los archivos adjuntos se enviarán a través de Google Drive por medio de una carpeta compartida.
