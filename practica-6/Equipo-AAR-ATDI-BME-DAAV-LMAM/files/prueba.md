este es un borrador

#### Explicacion de los pasos (luego redactamos esto bien xd)

## cración de redes

### Primero creamos la red WAN (la berde) NAT

https://redes-ciencias-unam.gitlab.io/laboratorio/practica-6/virtualbox-networks/

listamos las redes
```$ vboxmanage list natnets
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
Configuracion del adaptador vboxnet0

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
io ya lo tengo (y no c pk)
```
$ vboxmanage list intnets
Name:        intnet
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

### Habilitamos el servicio SSH

na mas le ponemos la opcion 14 xd

después hacemos ping con la opcion 7, escribimos 1.1.1.1, después volvemos a poner la opción 7 pero escribimos example.com

### Nos conetamos a pfSense 

con la dirección  https://192.168.42.254 y hacer toda esa madre

Después verificamos las actualizaciones

Una vez tengamos todo configurado guardamos el archivo en formato xml

Está guardado en carpeta "pfsense" y empieza con "1config-pfsense-AAR-..."

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
