## Pruebas de Conectividad de pfSense

✅ Conectividad de pfSense hacia Internet

- Hacia la dirección IP `1.1.1.1`

```
Enter a host name or IP address: 1.1.1.1
PING 1.1.1.1 (1.1.1.1): 56 data bytes
64 bytes from 1.1.1.1: icmp_seq=0 ttl=44 time=122.515 ms
64 bytes from 1.1.1.1: icmp_seq=1 ttl=44 time=247.314 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=44 time=159.485 ms

--- 1.1.1.1 ping statistics ---
3 packets transmitted, 3 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 122.515/176.438/247.314/52.341 ms
```

- Hacia el host `example.com`

```
Enter a host name or IP address: example.com

PING example.com (93.184.216.34): 56 data bytes
64 bytes from 93.184.216.34: icmp_seq=0 ttl=47 time=139.761 ms
64 bytes from 93.184.216.34: icmp_seq=1 ttl=47 time=152.867 ms
64 bytes from 93.184.216.34: icmp_seq=2 ttl=47 time=165.307 ms

--- example.com ping statistics ---
3 packets transmitted, 3 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 139.761/152.645/165.307/10.430 ms
```

✅ Conectividad entre pfSense y el cliente WAN (alpine)

```
Enter a host name or IP address: 10.0.2.5
PING 10.0.2.5 (10.0.2.5): 56 data bytes
64 bytes from 10.0.2.5: icmp_seq=0 ttl=64 time=0.611 ms
64 bytes from 10.0.2.5: icmp_seq=1 ttl=64 time=0.342 ms
64 bytes from 10.0.2.5: icmp_seq=2 ttl=64 time=0.327 ms

--- 10.0.2.5 ping statistics ---
3 packets transmitted, 3 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 0.327/0.427/0.611/0.130 ms
```