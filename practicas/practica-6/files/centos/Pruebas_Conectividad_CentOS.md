## Pruebas de conectividad de la red DMZ (CentOS)

1. Verificando la no-onectividad desde la red DMZ hacia LAN

```
[root@localhost ~]# ping -c 4 192.168.42.10
PING 192.168.42.10 (192.168.42.10) 56(84) bytes of data

--- 192.168.42.10 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3087ms
```

2. Verificando la resolución DNS

```
[root@localhost ~]# dig example.com.
; <<>> DiG 9.16.23-RH <<>> example.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 3605
;; flags: qr rd ra ad; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1432
;; QUESTION SECTION:
;example.com.			IN	A

;; ANSWER SECTION:
example.com.		19611	IN	A	93.184.216.34

;; Query time: 0 msec
;; SERVER: 172.16.1.254#53(172.16.1.254)
;; WHEN: Mon Apr 17 18:02:00 CST 2023
;; MSG SIZE  rcvd: 56
```

3. Pruebas de conectividad con PING

    - Red local 

    ```
    PING 192.168.0.5 (192.168.0.5) 56(84) bytes of data.
    64 bytes from 192.168.0.5: icmp_seq=1 ttl=62 time=0.624 ms
    64 bytes from 192.168.0.5: icmp_seq=2 ttl=62 time=0.563 ms
    64 bytes from 192.168.0.5: icmp_seq=3 ttl=62 time=0.568 ms
    64 bytes from 192.168.0.5: icmp_seq=4 ttl=62 time=0.599 ms

    --- 192.168.0.5 ping statistics ---
    4 packets transmitted, 4 received, 0% packet loss, time 3095ms
    rtt min/avg/max/mdev = 0.563/0.588/0.624/0.024 ms
    ```

    - Hacia otras redes

    ```
    PING 127.168.0.5 (127.168.0.5) 56(84) bytes of data.
    64 bytes from 127.168.0.5: icmp_seq=1 ttl=64 time=0.043 ms
    64 bytes from 127.168.0.5: icmp_seq=2 ttl=64 time=0.050 ms
    64 bytes from 127.168.0.5: icmp_seq=3 ttl=64 time=0.041 ms
    64 bytes from 127.168.0.5: icmp_seq=4 ttl=64 time=0.050 ms

    --- 127.168.0.5 ping statistics ---
    4 packets transmitted, 4 received, 0% packet loss, time 3066ms
    rtt min/avg/max/mdev = 0.041/0.046/0.050/0.004 ms
    ```

    - Hacia Internet

    ```
    PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
    64 bytes from 1.1.1.1: icmp_seq=1 ttl=43 time=265 ms
    64 bytes from 1.1.1.1: icmp_seq=2 ttl=43 time=54.1 ms
    64 bytes from 1.1.1.1: icmp_seq=3 ttl=43 time=107 ms
    64 bytes from 1.1.1.1: icmp_seq=4 ttl=43 time=134 ms

    --- 1.1.1.1 ping statistics ---
    4 packets transmitted, 4 received, 0% packet loss, time 3004ms
    rtt min/avg/max/mdev = 54.105/140.034/265.138/77.701 ms
    ```
