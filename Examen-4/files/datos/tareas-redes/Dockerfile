# syntax=docker/dockerfile:1.4

################################################################################

# Especifica el contenedor a usar como nueva imagen
FROM	docker.io/library/python:3.11-alpine AS python

# especifica el directorio del grupo de trabajo
WORKDIR	/srv

#Declara variables de entorno
ENV	GIT_PROJECT=Erickmarquez7\
	GIT_REPO=tareas-redes \
	GIT_BRANCH=entregas

ENV	ARCHIVE_FILE=${GIT_REPO}.tar.gz \
	GITLAB_URL="https://gitlab.com/${GIT_PROJECT}/${GIT_REPO}/-/archive/${GIT_BRANCH}/${GIT_REPO}-${GIT_BRANCH}.tar.gz"

# Ejecuta los comandos
RUN	wget -c -q -O ${ARCHIVE_FILE} ${GITLAB_URL} && \
	ls -l ${ARCHIVE_FILE} && \
	tar -xvzf ${ARCHIVE_FILE} --strip 1 && \
	rm -v ${ARCHIVE_FILE} && \
	pip3 config --global set global.progress_bar off && \
	pip3 install --upgrade pip && \
	pip3 install --requirement requirements.txt && \
	which mkdocs && \
	mkdocs build --strict && \
	ls -la .

################################################################################

# Especifica el contenedor a usar como nueva imagen
FROM	docker.io/library/nginx:1.23-alpine AS app

#Declara variables de entorno
ENV	NGINX_ROOT=/usr/share/nginx/html \
	MKDOCS_ROOT=/srv/public

# Crea la pagina indice
COPY	--from=python ${MKDOCS_ROOT} ${NGINX_ROOT}