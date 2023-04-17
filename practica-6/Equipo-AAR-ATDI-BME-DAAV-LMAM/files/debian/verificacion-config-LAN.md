erickdeb@Debian-11:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

#source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

#The primary network interfaces
#auto eth0
#allow-hotplug eth0
#iface eth0 inet dhcp 

auto eth1
allow-hotplug eth1
iface eth1 inet dhcp





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




erickdeb@Debian-11:~$ ip route 
default via 192.168.42.254 dev eth1 
169.254.0.0/16 dev eth1 scope link metric 1000 
192.168.42.0/24 dev eth1 proto kernel scope link src 192.168.42.10 




erickdeb@Debian-11:~$ cat /etc/resolv.conf 
domain local
search local
nameserver 192.168.42.254





erickdeb@Debian-11:~$  dig example.com. 

; <<>> DiG 9.16.37-Debian <<>> example.com.
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 50913
;; flags: qr rd ra ad; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1432
;; QUESTION SECTION:
;example.com.			IN	A

;; ANSWER SECTION:
example.com.		16571	IN	A	93.184.216.34

;; Query time: 0 msec
;; SERVER: 192.168.42.254#53(192.168.42.254)
;; WHEN: Sun Apr 16 21:54:37 CST 2023
;; MSG SIZE  rcvd: 56
         
         
         
         
         
         
erickdeb@Debian-11:~$ ping -c 4 1.1.1.1
PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
64 bytes from 1.1.1.1: icmp_seq=1 ttl=43 time=178 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=43 time=100 ms
64 bytes from 1.1.1.1: icmp_seq=3 ttl=43 time=125 ms
64 bytes from 1.1.1.1: icmp_seq=4 ttl=43 time=143 ms

--- 1.1.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 100.264/136.387/177.998/28.359 ms

