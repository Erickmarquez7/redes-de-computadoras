# Equipo-AAR-ATDI-BME-DAAV-LMAM

| Integrante                     | Número de Cuenta | Usuario de GitLab   |
|:------------------------------:|:----------------:|:-------------------:|
| Acosta Arzate Rubén            | 317205776        | `rubenAcostaArzate` |
| Alvarado Torres David Ignacio  | 316167613        | `ddalt`             |
| Bernal Marquez Erick           | 317042522        | `Erickmarquez7`     |
| Deloya Andrade Ana Valeria     | 317277582        | `avdeloya13`        |
| López Miranda Angel Mauricio   | 317034808        | `MauricioLMiranda`  |

# [Práctica 9](https://redes-ciencias-unam.gitlab.io/2023-2/laboratorio/practica-9/)

## Nombre de dominio que se registró y la dirección IP pública de la máquina virtual

http://waningnew.me/ 

68.218.33.216

## Explicación del procedimiento que se siguió para crear los nombres DNS en Azure

Iniciamos sesión en Azure, y damos click en *zonas DNS*

![](img/dns1.jpg)

Luego damos click en *waningnew.me*

![](img/dns2.jpg)

Seleccionamos la opción *Conjunto de registros*. Nos va a aparecer una pestaña del lado derecho con el nombre *Agregar conjunto de registros*, donde ponemos los datos de: nombre, tipo, dirección IP, etc.

![](img/dns3.jpg)

## Explicación de los comandos utilizados para instalar el servicio de Apache HTTPD y tramitar el certificado SSL

-- aqui va la explicacion xd, es explicar esto
https://redes-ciencias-unam.gitlab.io/laboratorio/practica-9/apache-httpd/

### Explica en tu reporte qué es lo que hace este bloque DirectoryMatch

-- aqui va la explicacion de esta madre https://redes-ciencias-unam.gitlab.io/laboratorio/practica-9/apache-httpd/#configuracion-de-seguridad-para-apache-httpd

### Explica en tu reporte por qué se recomienda establecer esos valores en las directivas

-- -- aqui va la explicacion de esta madre https://redes-ciencias-unam.gitlab.io/laboratorio/practica-9/apache-httpd/#configuracion-de-seguridad-para-apache-httpd


## Explicación la función de los scripts consulta-dns.sh, consulta-http.sh y consulta-ssl.sh

-- los podemos encontrar aqui, hasta abajo https://redes-ciencias-unam.gitlab.io/laboratorio/practica-9/#entregables

## Salida de las consultas DNS para los registros TXT, A y CNAME
(la salida txt puede cambiar porque es para el certificado SSL)

```
:~$ dig A waningnew.me

; <<>> DiG 9.18.1-1ubuntu1.2-Ubuntu <<>> A waningnew.me
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 1466
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;waningnew.me.			IN	A

;; ANSWER SECTION:
waningnew.me.		300	IN	A	68.218.33.216

;; Query time: 180 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Wed May 10 19:45:08 CST 2023
;; MSG SIZE  rcvd: 57
```

```
~$ dig CNAME tareas.waningnew.me

; <<>> DiG 9.18.1-1ubuntu1.2-Ubuntu <<>> CNAME tareas.waningnew.me
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 44575
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;tareas.waningnew.me.		IN	CNAME

;; ANSWER SECTION:
tareas.waningnew.me.	300	IN	CNAME	sitio.waningnew.me.

;; Query time: 148 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Wed May 10 19:47:44 CST 2023
;; MSG SIZE  rcvd: 68
```

```
~$ dig CNAME sitio.waningnew.me

; <<>> DiG 9.18.1-1ubuntu1.2-Ubuntu <<>> CNAME sitio.waningnew.me
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 45962
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;sitio.waningnew.me.		IN	CNAME

;; ANSWER SECTION:
sitio.waningnew.me.	300	IN	CNAME	waningnew.me.

;; Query time: 120 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Wed May 10 19:47:58 CST 2023
;; MSG SIZE  rcvd: 61
```

## Salida de las consultas HTTP para los sitios hospedados en el equipo

## Salida de las consultas SSL para los sitios hospedados en el equipo

