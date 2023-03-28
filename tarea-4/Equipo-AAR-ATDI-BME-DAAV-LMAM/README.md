# Equipo-AAR-ATDI-BME-DAAV-LMAM

| Integrante                     | Número de Cuenta | Usuario de GitLab   |
|:------------------------------:|:----------------:|:-------------------:|
| Acosta Arzate Rubén            | 317205776        | `rubenAcostaArzate` |
| Alvarado Torres David Ignacio  | 316167613        | `ddalt`             |
| Bernal Marquez Erick           | 317042522        | `Erickmarquez7`     |
| Deloya Andrade Ana Valeria     | 317277582        | `avdeloya13`        |
| López Miranda Angel Mauricio   | 317034808        | `MauricioLMiranda`  |

# [Tarea-4](https://redes-ciencias-unam.gitlab.io/2023-2/laboratorio/tarea-4/)


## Procedimiento

Primero revisamos que tengamos las herramientas instaladas en nuestro sistema, en el caso de linux ubutu

```
apt install wireshark
```

```
apt install tcpdump
```

```
apt install nmap
```

Estos comandos se encargan de instalar las herramientas necesarias utilizando el manejador de paquetes *apt*

## Dirección IP al servidor DHCP

### Renovamos IP
Desactivamos y volvemos a activar la configuración de la interfaz de red

```
ifdown "${IFACE}"
```
Desactiva la configuración

```
ifup "${IFACE}"
```
Activa la configuración

Donde *${IFACE}* es el nombre de nuestra interfaz de red

Desactivamos y volvemos a activar la conexión de red de Network Manager

```
nmcli connection down "${NAME}"
```
Desactiva la conexión

```
nmcli connection up "${NAME}"
```
Activa la conexión

Donde *${IFACE}* es el nombre de nuestra conexión de red

Solicitamos el servicio de DHCP

```
dhclient -r "${IFACE}"
```
Solicita el servicio DHCP

### Dirección local

Obtenemos dirección MAC e IP de la interfaz de red con cualquiera de los siguientes comandos

```
ifconfig -a
```
```
ip addr
```

Ambos comandos obtienen la dirección IP, solo que lo mustran de manera diferente

### Dirección del ruteador

Obtenemos la dirección del ruteador con cualquiera de los siguientes comandos

```
netstat -rn
```

```
route -n
```

```
ip route show
```

Los comandos obtienen la dirección IP, solo que lo mustran de manera diferente

### Dirección del servidor DNS

```
cat /etc/resolv.conf
```
Muestra el archivo resolv.conf

Este es un archivo resolv.conf dinámico para conectar clientes locales al sistema de resolución de stubs de DNS interno de systemd-resolved. Este archivo enumera todos los dominios de búsqueda configurados.

```
nmcli connection show "${NAME}" | grep -i DNS
```
Muestra las direcciónes IPv4 y/o IPv6 del servidor DNS para nuestra conexión de red de Network Manager

## Captura de trafico

En cada capa debemos capturar el tráfico de red. Para ello identificamos la interfaz por la cual nos conectamos a intenet ya sea de manera alámbrica o inalámbrica con comandos ya utilizados

```
ifconfig -a
```

```
ip addr
```

Capturaremos el tráfico con WireShark para verlo de manera más visual
Seleccionamos nuestra interfaz de red junto con un filtro, haremos una prueba con nuestra dirección IP *net 192.168.0.0/24*

| ![](img/wire-filtro-prueba.png)
|:-------------------------:|
| Filtro de prueba

La captura del tráfico

| ![](img/wire-captura-prueba.png)
|:-------------------------:|
| Captura de tráfico de prueba

### Limpiar tabla ARP

Para cada captura de tráfico de red debemos limpiar la tabla ARP. Mostraremos cómo hacerlo

```
ip neighbour flush all
```
Vacia los objetos vecinos que establecen enlaces, no se ejecuta cuando no se proporcionan argumentos y que los estados vecinos predeterminados que se vaciarán no incluyen **permanent** ni **noarp**

https://man7.org/linux/man-pages/man8/ip-neighbour.8.html

### Mostrar tabla ARP

Mostramos la tabla ARP de la maquina fisica al finalizar el tráfico con cualquiera de los dos comandos

```
arp -an
```

```
ip neighbour show
```

Ambos muestra la tabla ARP

### Limpar caché DNS

Para cada captura de tráfico de red debemos limpiar el caché DNS. Mostraremos cómo hacerlo.

```
systemd-resolve --flush-caches
```

```
resolvectl flush-caches
```

```
service dnsmasq restart
```
Cualquiera de los siguientes comandos limpian el caché DNS

Podemos consultar el servidor DNS con las siguientes sintaxis

```
dig  [TIPO]  NOMBRE  @SERVIDOR
dig example.com. @one.one.one.one
dig AAAA example.com. @1.1.1.1
dig A example.com. @2606:4700:4700::1111

nslookup  [-type=TIPO]  NOMBRE  SERVIDOR
nslookup example.com. one.one.one.one
nslookup -type=A example.com. 1.1.1.1
nslookup -type=AAAA example.com. 2606:4700:4700::1111
```

(en conclusión para cada capa
limpiar tabla ARP
limpiar Caché DNS
captura de trafico
mostrar tabla ARP
)



## Pruebas de conectividad

### Capa 2 - Enlace



### Capa 3 - Red
ping -c 10 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=1.91 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=1.54 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=2.07 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=2.17 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=64 time=1.76 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=64 time=1.90 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=64 time=2.02 ms
64 bytes from 192.168.0.1: icmp_seq=8 ttl=64 time=1.40 ms
64 bytes from 192.168.0.1: icmp_seq=9 ttl=64 time=2.03 ms
64 bytes from 192.168.0.1: icmp_seq=10 ttl=64 time=2.05 ms

--- 192.168.0.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9014ms
rtt min/avg/max/mdev = 1.402/1.884/2.172/0.234 ms

ping6 -c 10 fe80::bdc6:e097:c0ab:cb5f
PING fe80::bdc6:e097:c0ab:cb5f(fe80::bdc6:e097:c0ab:cb5f) 56 data bytes

--- fe80::bdc6:e097:c0ab:cb5f ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9217ms


ping  -c 10 one.one.one.one
PING one.one.one.one (1.0.0.1) 56(84) bytes of data.
64 bytes from one.one.one.one (1.0.0.1): icmp_seq=1 ttl=47 time=37.1 ms
64 bytes from one.one.one.one (1.0.0.1): icmp_seq=2 ttl=47 time=33.6 ms
64 bytes from one.one.one.one (1.0.0.1): icmp_seq=3 ttl=47 time=34.9 ms
64 bytes from one.one.one.one (1.0.0.1): icmp_seq=4 ttl=47 time=42.3 ms
64 bytes from one.one.one.one (1.0.0.1): icmp_seq=5 ttl=47 time=29.1 ms
64 bytes from one.one.one.one (1.0.0.1): icmp_seq=6 ttl=47 time=36.3 ms
64 bytes from one.one.one.one (1.0.0.1): icmp_seq=7 ttl=47 time=33.3 ms
64 bytes from one.one.one.one (1.0.0.1): icmp_seq=8 ttl=47 time=39.0 ms
64 bytes from one.one.one.one (1.0.0.1): icmp_seq=9 ttl=47 time=33.1 ms
64 bytes from one.one.one.one (1.0.0.1): icmp_seq=10 ttl=47 time=34.4 ms

--- one.one.one.one ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9013ms
rtt min/avg/max/mdev = 29.084/35.307/42.252/3.433 ms

ping  -c 10 www.fciencias.unam.mx
PING pagina.fciencias.unam.mx (132.248.181.220) 56(84) bytes of data.
64 bytes from pagina.fciencias.unam.mx (132.248.181.220): icmp_seq=1 ttl=47 time=44.8 ms
64 bytes from pagina.fciencias.unam.mx (132.248.181.220): icmp_seq=2 ttl=47 time=49.6 ms
64 bytes from pagina.fciencias.unam.mx (132.248.181.220): icmp_seq=3 ttl=47 time=37.1 ms
64 bytes from pagina.fciencias.unam.mx (132.248.181.220): icmp_seq=4 ttl=47 time=37.9 ms
64 bytes from pagina.fciencias.unam.mx (132.248.181.220): icmp_seq=5 ttl=47 time=40.3 ms
64 bytes from pagina.fciencias.unam.mx (132.248.181.220): icmp_seq=6 ttl=47 time=37.2 ms
64 bytes from pagina.fciencias.unam.mx (132.248.181.220): icmp_seq=7 ttl=47 time=40.7 ms
64 bytes from pagina.fciencias.unam.mx (132.248.181.220): icmp_seq=8 ttl=47 time=35.5 ms
64 bytes from pagina.fciencias.unam.mx (132.248.181.220): icmp_seq=9 ttl=47 time=39.0 ms
64 bytes from pagina.fciencias.unam.mx (132.248.181.220): icmp_seq=10 ttl=47 time=40.6 ms

--- pagina.fciencias.unam.mx ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9011ms
rtt min/avg/max/mdev = 35.504/40.266/49.581/3.955 ms

traceroute  -n one.one.one.one
traceroute to one.one.one.one (1.1.1.1), 30 hops max, 60 byte packets
 1  192.168.0.1  2.531 ms  3.264 ms  3.838 ms
 2  10.221.224.1  22.769 ms  28.063 ms  28.335 ms
 3  100.65.0.255  26.860 ms !N * *

traceroute  -n www.fciencias.unam.mx
traceroute to www.fciencias.unam.mx (132.248.181.220), 30 hops max, 60 byte packets
 1  192.168.0.1  2.023 ms  2.723 ms  3.676 ms
 2  10.221.224.1  22.714 ms  22.991 ms  23.243 ms
 3  100.65.0.253  23.670 ms !N * *

; <<>> DiG 9.18.1-1ubuntu1.3-Ubuntu <<>> unam.mx @one.one.one.one
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 7714
;; flags: qr rd ra ad; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
;; QUESTION SECTION:
;unam.mx.                       IN      A

;; ANSWER SECTION:
unam.mx.                2127    IN      A       132.248.166.20
unam.mx.                2127    IN      A       132.248.166.18
unam.mx.                2127    IN      A       132.248.166.19
unam.mx.                2127    IN      A       132.248.166.17

;; Query time: 35 msec
;; SERVER: 1.1.1.1#53(one.one.one.one) (UDP)
;; WHEN: Mon Mar 27 23:43:13 CST 2023
;; MSG SIZE  rcvd: 100



### Capa 4 - Transporte

### Capa 7 - Aplicación
