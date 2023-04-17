## Pruebas de conectividad de la red LAN (Debian)

1. Verificando la resolución DNS
```
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

2. Verificando la conectividad ICMP (desde el cliente LAN hacia Internet)

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

3. Verificando la conectividad de la red LAN hacia DMZ

Hacia la dirección IP `1.1.1.1`

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
```