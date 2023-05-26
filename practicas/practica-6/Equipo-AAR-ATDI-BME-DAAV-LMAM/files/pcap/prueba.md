
## Creación de redes

### Primero creamos la red WAN (la berde) NAT

https://redes-ciencias-unam.gitlab.io/laboratorio/practica-6/virtualbox-networks/

listamos las redes

```
$ vboxmanage list natnets
Name:         NatNetwork
Network:      10.0.2.0/24
Gateway:      10.0.2.1
DHCP Server:  Yes
IPv6:         No
IPv6 Prefix:  
IPv6 Default: No
```

### Ahora la red LAN (la azul) host-only
Creamos /etc/vbox y seguimos los pasos de la pagina xd
lo del archivo .conf

(como en la tarea 1 ya teniamos un vboxnet0 entonces configuré la 1 xd pa ver si al rato la elimino xd)
Comprobacion de la consola xd

```
$ vboxmanage list hostonlyifs
Name:            vboxnet0
GUID:            786f6276-656e-4074-8000-0a0027000000
DHCP:            Disabled
IPAddress:       192.168.42.1
NetworkMask:     255.255.255.0
IPV6Address:     
IPV6NetworkMaskPrefixLength: 0
HardwareAddress: 0a:00:27:00:00:00
MediumType:      Ethernet
Wireless:        No
Status:          Up
VBoxNetworkName: HostInterfaceNetworking-vboxnet0
```
### Configuracion del adaptador vboxnet0

```
$ ip addr show dev vboxnet0
4: vboxnet0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 0a:00:27:00:00:00 brd ff:ff:ff:ff:ff:ff
    inet 192.168.42.1/24 brd 192.168.42.255 scope global vboxnet0
       valid_lft forever preferred_lft forever
```
verificar lo de down o up

```
$ ip route show dev vboxnet0
192.168.42.0/24 proto kernel scope link src 192.168.42.1 linkdown 
```

### ahora la DMZ (naranja) internal network

```
$ vboxmanage list intnets
Name:        intnet
```
### Conectividad desde la red LAN hacia DMZ
```
erickdeb@Debian-11:~$ ping -c 4 1.1.1.1
PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
64 bytes from 1.1.1.1: icmp_seq=1 ttl=43 time=58.0 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=43 time=59.4 ms
64 bytes from 1.1.1.1: icmp_seq=3 ttl=43 time=66.6 ms
64 bytes from 1.1.1.1: icmp_seq=4 ttl=43 time=50.0 ms

--- 1.1.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 49.994/58.507/66.621/5.905 ms
```

### Conectividad desde la red DMZ hacia LAN

```
[root@localhost ~]# ping -c 4 192.168.42.10
PING 192.168.42.10 (192.168.42.10) 56(84) bytes of data

--- 192.168.42.10 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3087ms
```

## lo de pfsense

Si les da error aquí lo solucioné xd 
https://www.reddit.com/r/PFSENSE/comments/65u4ro/is_the_targz_broken/

después de la instalación se confiuguran las redes en pfSense mediante las interfaces de red

Asiganmos interfaces y después configuramos las IP

Primero la WAN, con dhcp

luego LAN estática, y un rango de dhcp 192.168.42.100 - 192.168.42.199
Esto nos va porporciona una interfaz web de pfSense que podemos acceder para su configuración

por ultimo la OPT con dirección 172.16.1.254/24. pero no habilitamos el dhcp

### Conectividad de pfSense hacia Internet

```
Enter a host name or IP address: 1.1.1.1
PING 1.1.1.1 (1.1.1.1): 56 data bytes
64 bytes from 1.1.1.1: icmp_seq=0 ttl=44 time=122.515 ms
64 bytes from 1.1.1.1: icmp_seq=1 ttl=44 time=247.314 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=44 time=159.485 ms

--- 1.1.1.1 ping statistics ---
3 packets transmitted, 3 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 122.515/176.438/247.314/52.341 ms

Enter a host name or IP address: example.com
PING example.com (93.184.216.34): 56 data bytes
64 bytes from 93.184.216.34: icmp_seq=0 ttl=47 time=139.761 ms
64 bytes from 93.184.216.34: icmp_seq=1 ttl=47 time=152.867 ms
64 bytes from 93.184.216.34: icmp_seq=2 ttl=47 time=165.307 ms

--- example.com ping statistics ---
3 packets transmitted, 3 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 139.761/152.645/165.307/10.430 ms
```

### Conectividad entre pfSense y el cliente WAN (alpine)

```
Enter a host name or IP address: 10.0.2.5
PING 10.0.2.5 (10.0.2.5): 56 data bytes
64 bytes from 10.0.2.5: icmp_seq=0 ttl=64 time=0.611 ms
64 bytes from 10.0.2.5: icmp_seq=1 ttl=64 time=0.342 ms
64 bytes from 10.0.2.5: icmp_seq=2 ttl=64 time=0.327 ms

--- 10.0.2.5 ping statistics ---
3 packets transmitted, 3 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 0.327/0.427/0.611/0.130 ms
```

### Conectividad del cliente LAN (Debian) hacia Internet

```
erickdeb@Debian-11:~$ ping -c 4 1.1.1.1
PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
64 bytes from 1.1.1.1: icmp_seq=1 ttl=43 time=121 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=43 time=137 ms
64 bytes from 1.1.1.1: icmp_seq=3 ttl=43 time=157 ms
64 bytes from 1.1.1.1: icmp_seq=4 ttl=43 time=179 ms

--- 1.1.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 185ms
rtt min/avg/max/mdev = 120.535/148.361/179.414/22.017 ms


erickdeb@Debian-11:~$ dig example.com

; <<>> DiG 9.16.37-Debian <<>> example.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 23315
;; flags: qr rd ra ad; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1432
;; QUESTION SECTION:
;example.com.			IN	A

;; ANSWER SECTION:
example.com.		21391	IN	A	93.184.216.34

;; Query time: 0 msec
;; SERVER: 192.168.42.254#53(192.168.42.254)
;; WHEN: Mon Apr 17 00:02:41 CST 2023
;; MSG SIZE  rcvd: 56
```

### Conectividad del serivdor DMZ (CentOS) hacia Internet

```
[root@localhost ~]# ping -c 4 1.1.1.1
PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
64 bytes from 1.1.1.1: icmp_seq=1 ttl=43 time=237 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=43 time=156 ms
64 bytes from 1.1.1.1: icmp_seq=3 ttl=43 time=08.6 ms
64 bytes from 1.1.1.1: icmp_seq=4 ttl=43 time=101 ms

--- 1.1.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 80.568/143.651/236.687/60.390 ms


[root@localhost ~]# ping -c 4 example.com
PING example.com (93.184.216.34) 56(84) bytes of data.
64 bytes from 93.184.216.34: icmp_seq=1 ttl=46 time=145 ms
64 bytes from 93.184.216.34: icmp_seq=2 ttl=46 time=74.6 ms
64 bytes from 93.184.216.34: icmp_seq=3 ttl=46 time=87.7 ms
64 bytes from 93.184.216.34: icmp_seq=4 ttl=46 time=111 ms

--- example.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 74.571/104.507/144.740/26.653 ms
```

### Habilitamos el servicio 

Unicamente seleccionamos la opcion 14 

después hacemos ping con la opcion 7, escribimos 1.1.1.1, después volvemos a poner la opción 7 pero escribimos example.com

### Nos conetamos a pfSense 

con la dirección  https://192.168.42.254 y hacer toda esa madre

Después verificamos las actualizaciones

Una vez tengamos todo configurado guardamos el archivo en formato xml

Guardado en carpeta "pfsense" y empieza con "1config-pfsense-AAR-..."

### Configuración del pfSense

Todo esto se hace en la pagina de pfSense 

Configuramos las redes para permitir tráfico de redes no homologadas

Luego el serivico DNS y los alias para SSH, HTTP y HTTPS.

Después xd el acceso al servicio de SSH, HHTP, HTTPS en la red DMZ (Port forward)

Por ultimo establecemos reglas pdel firewall para cada una de las redes WAN, LAN y DMZ

La configuración se encuentra en la carpeta de files/pfsense en el archivo "2config-pfsense-AAR-..."

## Después de eso sigue la instalación de alpine 

ps seguir los pasos tal cual, aunque en mi caso me dio la dirección 10.0.2.5 y no 10.0.2.4

Para la parte de inicio de sessión remoto debe ser en la maquina fisica

Para conectarse es [usuario]@localhost

Y para sudo pues kien sabe la dvd no me aparece el sudo, mas bien doas pero aun así no jala, F.
