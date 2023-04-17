## Verificación de la configuración del cliente LAN (Debian)

1. Configurando el archivo `/etc/network/interfaces` para pedir una dirección IP por medio de DHCP en la red LAN:

```
erickdeb@Debian-11:~$ cat /etc/network/interfaces

## This file describes the network interfaces available on your system
## and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

## The loopback network interface

```
auto lo
iface lo inet loopback
```

## The primary network interfaces
## auto eth0
## allow-hotplug eth0
## iface eth0 inet dhcp 

```
auto eth1
allow-hotplug eth1
iface eth1 inet dhcp
```
2. Verificando que el adaptador de red `eth1` conectado a la red LAN tenga una dirección IP del segmento `192.168.42.0/24`:

```
erickdeb@Debian-11:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether 08:00:27:42:18:93 brd ff:ff:ff:ff:ff:ff
    altname enp0s3
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:46:f7:fc brd ff:ff:ff:ff:ff:ff
    altname enp0s8
    inet 192.168.42.10/24 brd 192.168.42.255 scope global dynamic eth1
       valid_lft 557sec preferred_lft 557sec
    inet6 fe80::a00:27ff:fe46:f7fc/64 scope link 
       valid_lft forever preferred_lft forever
```

3. Verificando que la máquina virtual tenga configurado un _gateway_ para comunicarse con otras redes:

```
erickdeb@Debian-11:~$ ip route 
default via 192.168.42.254 dev eth1 
169.254.0.0/16 dev eth1 scope link metric 1000 
192.168.42.0/24 dev eth1 proto kernel scope link src 192.168.42.10 
```

4. Verificando que el archivo `/etc/resolv.conf` tenga configurado el servidor DNS que se obtuvo por DHCP:

```
erickdeb@Debian-11:~$ cat /etc/resolv.conf 
domain local
search local
nameserver 192.168.42.254
```

5. Verificando conectividad a internet:

Las pruebas de conectividad a internet, incluyendo la resolución DNS y la conectividad ICMP, se encuentran en el siguiente archivo: [Pruebas_Conectividad_Debian.md](Pruebas_Conectividad_Debian.md)
