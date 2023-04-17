
## Verificación de la configuración del cliente WAN (Alpine)

```
alpine:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

```
alpine:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 08:00:27:fa:42:b8 brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.5/24 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fefa:42b8/64 scope link 
       valid_lft forever preferred_lft forever
```

```
alpine:~$ ip route
default via 10.0.2.1 dev eth0  metric 202 
10.0.2.0/24 dev eth0 scope link  src 10.0.2.5 
```

```
alpine:~$ cat /etc/resolv.conf
search .
nameserver 10.0.2.1
```

Las pruebas de conectividad a internet, incluyendo la resolución DNS y la conectividad ICMP, se encuentran en el siguiente archivo: [Pruebas_Conectividad_Alpine.md](Pruebas_Conectividad_Alpine.md)
