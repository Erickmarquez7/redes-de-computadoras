## Pruebas de conectividad de la red WAN (Alpine)

1. Verificando la resolución DNS

```
alpine:~# dig example.com.
; <<>> DiG 9.18.13 <<>> example.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 2376
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;example.com.			IN	A

;; ANSWER SECTION:
example.com.		7168	IN	A	93.184.216.34

;; Query time: 0 msec
;; SERVER: 10.0.2.1#53(10.0.2.1) (UDP)
;; WHEN: Mon Apr 17 17:57:04 CST 2023
;; MSG SIZE  rcvd: 56
```

2. Pruebas de conectividad con PING

    - Red local 

    ```
    PING 192.168.0.5 (192.168.0.5): 56 data bytes
    64 bytes from 192.168.0.5: seq=0 ttl=63 time=0.333 ms
    64 bytes from 192.168.0.5: seq=1 ttl=63 time=0.258 ms
    64 bytes from 192.168.0.5: seq=2 ttl=63 time=0.286 ms
    64 bytes from 192.168.0.5: seq=3 ttl=63 time=0.259 ms

    --- 192.168.0.5 ping statistics ---
    4 packets transmitted, 4 packets received, 0% packet loss
    round-trip min/avg/max = 0.258/0.284/0.333 ms
    ```

    - Hacia otras redes

    ```
    PING 127.168.0.5 (127.168.0.5): 56 data bytes
    64 bytes from 127.168.0.5: seq=0 ttl=64 time=0.044 ms
    64 bytes from 127.168.0.5: seq=1 ttl=64 time=0.057 ms
    64 bytes from 127.168.0.5: seq=2 ttl=64 time=0.058 ms
    64 bytes from 127.168.0.5: seq=3 ttl=64 time=0.055 ms

    --- 127.168.0.5 ping statistics ---
    4 packets transmitted, 4 packets received, 0% packet loss
    round-trip min/avg/max = 0.044/0.053/0.058 ms
    ```

    - Hacia Internet

    ```
    PING 1.1.1.1 (1.1.1.1): 56 data bytes
    64 bytes from 1.1.1.1: seq=0 ttl=44 time=69.700 ms
    64 bytes from 1.1.1.1: seq=1 ttl=44 time=149.367 ms
    64 bytes from 1.1.1.1: seq=2 ttl=44 time=71.598 ms
    64 bytes from 1.1.1.1: seq=3 ttl=44 time=93.615 ms

    --- 1.1.1.1 ping statistics ---
    4 packets transmitted, 4 packets received, 0% packet loss
    round-trip min/avg/max = 69.700/96.070/149.367 ms
    ```
