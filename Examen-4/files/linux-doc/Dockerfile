# syntax=docker/dockerfile:1.4

################################################################################

# Especifica el contenedor a usar como nueva imagen
FROM	docker.io/library/debian:11 AS debian

#Declara variables de entorno
ENV	DEBIAN_FRONTEND=noninteractive

# Elige alguna de las dos opciones
#
# Opción A:
#   Copiar un archivo existente en el directorio a una ruta en el contenedor
#   Esta opción es compatible con **cualquier versión** de Docker

# Optamos por esta opción para que no haya problemas entre distintas versiones de los integrantes del equipo
# el archivo apt-conf-99-local.conf fue proporcionado y contiene lo mismo que la opción B, solo que es un archivo diferente. Se encarga de copiar los datos al segundo archivo

# Crea la pagina indice
COPY	apt-conf-99-local.conf  /etc/apt/apt.conf.d/99-local

# Opción B:
#   Utilizar la nueva sintaxis _HereDoc_ para especificar el contenido del archivo en el Dockerfile
#   Esta opción es compatible con **versiones recientes** de Docker
#COPY	<<EOF  /etc/apt/apt.conf.d/99-local
#quiet "2";
#APT::Get::Assume-Yes "1";
#APT::Install-Recommends "0";
#APT::Install-Suggests "0";
#APT::Color "0";
#Dpkg::Progress "0";
#Dpkg::Progress-Fancy "0";
#EOF

# Ejecuta los comandos
RUN	apt update && \
	apt install linux-doc

################################################################################

# Especifica el contenedor a usar como nueva imagen
FROM	docker.io/library/nginx:1.23-alpine AS app

#Declara variables de entorno
ENV	NGINX_ROOT=/usr/share/nginx/html \
	LINUX_DOC_ROOT=/usr/share/doc/linux-doc/html

# Crea la pagina indice
COPY	--from=debian ${LINUX_DOC_ROOT} ${NGINX_ROOT}