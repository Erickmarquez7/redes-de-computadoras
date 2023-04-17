## Pruebas de conectividad de la red DMZ (CentOS)

1. Verificando la no-onectividad desde la red DMZ hacia LAN

```
[root@localhost ~]# ping -c 4 192.168.42.10
PING 192.168.42.10 (192.168.42.10) 56(84) bytes of data

--- 192.168.42.10 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3087ms
```

2. Verificando la conectividad ICMP (del serivdor DMZ (CentOS) hacia Internet)

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
```

```
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