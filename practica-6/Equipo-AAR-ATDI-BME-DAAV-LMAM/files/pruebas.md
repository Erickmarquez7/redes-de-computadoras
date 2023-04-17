✅ Conectividad desde la red LAN hacia DMZ

erickdeb@Debian-11:~$ ping -c 4 1.1.1.1
PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
64 bytes from 1.1.1.1: icmp_seq=1 ttl=43 time=58.0 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=43 time=59.4 ms
64 bytes from 1.1.1.1: icmp_seq=3 ttl=43 time=66.6 ms
64 bytes from 1.1.1.1: icmp_seq=4 ttl=43 time=50.0 ms

--- 1.1.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 49.994/58.507/66.621/5.905 ms


❌ Conectividad desde la red DMZ hacia LAN
[root@localhost ~]# ping -c 4 192.168.42.10
PING 192.168.42.10 (192.168.42.10) 56(84) bytes of data

--- 192.168.42.10 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3087ms


✅ Conectividad de pfSense hacia Internet
Enter a host name or IP address: 1.1.1.1
PING 1.1.1.1 (1.1.1.1): 56 data bytes
64 bytes from 1.1.1.1: icmp_seq=0 ttl=44 time=122.515 ms
64 bytes from 1.1.1.1: icmp_seq=1 ttl=44 time=247.314 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=44 time=159.485 ms

--- 1.1.1.1 ping statistics ---
3 packets transmitted, 3 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 122.515/176.438/247.314/52.341 ms


Enter a host name or IP address: example.com

PING example.com (93.184.216.34): 56 data bytes
64 bytes from 93.184.216.34: icmp_seq=0 ttl=47 time=139.761 ms
64 bytes from 93.184.216.34: icmp_seq=1 ttl=47 time=152.867 ms
64 bytes from 93.184.216.34: icmp_seq=2 ttl=47 time=165.307 ms

--- example.com ping statistics ---
3 packets transmitted, 3 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 139.761/152.645/165.307/10.430 ms


✅ Conectividad entre pfSense y el cliente WAN (alpine)
Enter a host name or IP address: 10.0.2.5
PING 10.0.2.5 (10.0.2.5): 56 data bytes
64 bytes from 10.0.2.5: icmp_seq=0 ttl=64 time=0.611 ms
64 bytes from 10.0.2.5: icmp_seq=1 ttl=64 time=0.342 ms
64 bytes from 10.0.2.5: icmp_seq=2 ttl=64 time=0.327 ms

--- 10.0.2.5 ping statistics ---
3 packets transmitted, 3 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 0.327/0.427/0.611/0.130 ms



✅ Conectividad del cliente LAN (Debian) hacia Internet
erickdeb@Debian-11:~$ ping -c 4 1.1.1.1
PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
64 bytes from 1.1.1.1: icmp_seq=1 ttl=43 time=121 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=43 time=137 ms
64 bytes from 1.1.1.1: icmp_seq=3 ttl=43 time=157 ms
64 bytes from 1.1.1.1: icmp_seq=4 ttl=43 time=179 ms

--- 1.1.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 185ms
rtt min/avg/max/mdev = 120.535/148.361/179.414/22.017 ms


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

✅ Conectividad del serivdor DMZ (CentOS) hacia Internet
[root@localhost ~]# ping -c 4 1.1.1.1
PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
64 bytes from 1.1.1.1: icmp_seq=1 ttl=43 time=237 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=43 time=156 ms
64 bytes from 1.1.1.1: icmp_seq=3 ttl=43 time=08.6 ms
64 bytes from 1.1.1.1: icmp_seq=4 ttl=43 time=101 ms

--- 1.1.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 80.568/143.651/236.687/60.390 ms


[root@localhost ~]# ping -c 4 example.com
PING example.com (93.184.216.34) 56(84) bytes of data.
64 bytes from 93.184.216.34: icmp_seq=1 ttl=46 time=145 ms
64 bytes from 93.184.216.34: icmp_seq=2 ttl=46 time=74.6 ms
64 bytes from 93.184.216.34: icmp_seq=3 ttl=46 time=87.7 ms
64 bytes from 93.184.216.34: icmp_seq=4 ttl=46 time=111 ms

--- example.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 74.571/104.507/144.740/26.653 ms


✅ Conectividad del cliente WAN (alpine) al servidor DMZ (CentOS) utilizando la redirección de puertos

    ✅ Servicio SSH
    ✅ Servicios HTTP y HTTPS

