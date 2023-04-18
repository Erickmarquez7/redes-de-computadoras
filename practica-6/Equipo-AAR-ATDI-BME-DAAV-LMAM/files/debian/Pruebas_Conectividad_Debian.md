## Pruebas de conectividad de la red LAN (Debian)

1. Verificando la resolución DNS
```
erickdeb@Debian-11:~$ dig example.com
; <<>> DiG 9.16.37-Debian <<>> example.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 22851
;; flags: qr rd ra ad; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1432
;; QUESTION SECTION:
;example.com.			IN	A

;; ANSWER SECTION:
example.com.		20026	IN	A	93.184.216.34

;; Query time: 4 msec
;; SERVER: 192.168.42.254#53(192.168.42.254)
;; WHEN: Mon Apr 17 17:55:05 CST 2023
;; MSG SIZE  rcvd: 56
```

2. Pruebas de conectividad con PING

    - Red local 

    ```
    PING 192.168.0.5 (192.168.0.5): 56 data bytes
    64 bytes from 192.168.0.5: icmp_seq=0 ttl=62 time=0.635 ms
    64 bytes from 192.168.0.5: icmp_seq=1 ttl=62 time=0.539 ms
    64 bytes from 192.168.0.5: icmp_seq=2 ttl=62 time=0.542 ms
    64 bytes from 192.168.0.5: icmp_seq=3 ttl=62 time=0.614 ms
    
    --- 192.168.0.5 ping statistics ---
    4 packets transmitted, 4 packets received, 0% packet loss
    round-trip min/avg/max/stddev = 0.539/0.583/0.635/0.043 ms
    ```

    - Hacia otras redes

    ```
    PING 127.168.0.5 (127.168.0.5): 56 data bytes
    64 bytes from 127.168.0.5: icmp_seq=0 ttl=64 time=0.050 ms
    64 bytes from 127.168.0.5: icmp_seq=1 ttl=64 time=0.058 ms
    64 bytes from 127.168.0.5: icmp_seq=2 ttl=64 time=0.055 ms
    64 bytes from 127.168.0.5: icmp_seq=3 ttl=64 time=0.050 ms

    --- 127.168.0.5 ping statistics ---
    4 packets transmitted, 4 packets received, 0% packet loss
    round-trip min/avg/max/stddev = 0.050/0.053/0.058/0.000 ms
    ```

    - Hacia Internet

    ```
    PING 1.1.1.1 (1.1.1.1): 56 data bytes
    64 bytes from 1.1.1.1: icmp_seq=0 ttl=43 time=120.223 ms
    64 bytes from 1.1.1.1: icmp_seq=1 ttl=43 time=143.078 ms
    64 bytes from 1.1.1.1: icmp_seq=2 ttl=43 time=59.196 ms
    64 bytes from 1.1.1.1: icmp_seq=3 ttl=43 time=83.444 ms
    --- 1.1.1.1 ping statistics ---
    4 packets transmitted, 4 packets received, 0% packet loss
    round-trip min/avg/max/stddev = 59.196/101.485/143.078/32.384 ms
    ```
