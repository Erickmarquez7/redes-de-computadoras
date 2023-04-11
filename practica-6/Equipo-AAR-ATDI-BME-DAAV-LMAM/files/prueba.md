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
