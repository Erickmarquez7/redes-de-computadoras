
## Configuracion red WAN

### Verificacion del cliente alpine tenga la dirección IP del segmento WAN

```
alpine:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

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


alpine:~$ ip route
default via 10.0.2.1 dev eth0  metric 202 
10.0.2.0/24 dev eth0 scope link  src 10.0.2.5 


alpine:~$ cat /etc/resolv.conf
search .
nameserver 10.0.2.1


alpine:~# dig example.com.

; <<>> DiG 9.18.13 <<>> example.com.
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 20350
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;example.com.			IN	A

;; ANSWER SECTION:
example.com.		18438	IN	A	93.184.216.34

;; Query time: 140 msec
;; SERVER: 10.0.2.1#53(10.0.2.1) (UDP)
;; WHEN: Sun Apr 16 21:53:02 CST 2023
;; MSG SIZE  rcvd: 56


alpine:~# ping -c 4 1.1.1.1
PING 1.1.1.1 (1.1.1.1): 56 data bytes
64 bytes from 1.1.1.1: seq=0 ttl=44 time=167.114 ms
64 bytes from 1.1.1.1: seq=1 ttl=44 time=85.812 ms
64 bytes from 1.1.1.1: seq=2 ttl=44 time=319.069 ms
64 bytes from 1.1.1.1: seq=3 ttl=44 time=130.147 ms

--- 1.1.1.1 ping statistics ---
4 packets transmitted, 4 packets received, 0% packet loss
round-trip min/avg/max = 85.812/175.535/319.069 ms
```
