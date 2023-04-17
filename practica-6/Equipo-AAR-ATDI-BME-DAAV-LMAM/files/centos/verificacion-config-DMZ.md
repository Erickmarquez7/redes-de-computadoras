
## Configuracion red DMZ

### Verificacion del servidor CentOS tenga la dirección IP estática

```
[root@localhost ~]# nmcli connection show 
NAME      	    UUID                                  TYPE      DEVICE
eth1-dmz  	    3de1d762-337e-430f-b322-33adc0910b09  ethernet  eth1
lo 	  	    e4498bda-7719-4f05-98a2-af9793695a19  ethernet  lo
enp0s3	  	    88ee6a6c-0507-309b-85d2-7d8b3f8a3f6e  ethernet  --
eth1      	    2a51a8ce-619d-3da8-a93e-ed46c3ced639  ethernet  --
Wired connection 1  ddaba1sa-5f7a-3ba0-8b30-fa7fba4171c4  ethernet  --


[root@localhost ~]# hostname -I
172.16.1.10


[root@localhost ~]# ip route
default via 172.16.1.254 dev eth1 proto static metric 100
172.16.1.0/24 dev eth1 proto kernel scope link src 172.16.1.10 metric 100


[root@localhost ~]# cat /etc/resolv.conf
nameserver 172.16.1.254


[root@localhost ~]# ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 08:00:27:7f:93:ce brd ff:ff:ff:ff:ff:ff
    altname enp0s3
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:d1:02:fa brd ff:ff:ff:ff:ff:ff
    altname enp0s8
    inet 172.16.1.10/24 brd 172.16.1.255 scope global noprefixroute eth1
       valid_lft forever preferred_lft forever
    inet6 fe80::4df6:72b4:4211:8c91/64 scope link noprefixroute
       valid_lft forever preferred_lft forever

```
