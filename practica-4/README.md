# Equipo-AAR-ATDI-BME-DAAV-LMAM

| Integrante                     | Número de Cuenta | Usuario de GitLab   |
|:------------------------------:|:----------------:|:-------------------:|
| Acosta Arzate Rubén            | 317205776        | `rubenAcostaArzate` |
| Alvarado Torres David Ignacio  | 316167613        | `ddalt`             |
| Bernal Marquez Erick           | 317042522        | `Erickmarquez7`     |
| Deloya Andrade Ana Valeria     | 317277582        | `avdeloya13`        |
| López Miranda Angel Mauricio   | 317034808        | `MauricioLMiranda`  |

# [Practica-4](https://redes-ciencias-unam.gitlab.io/2023-2/laboratorio/practica-4/)

En este enlace se encuentra el archivo `.pkt` de la práctica: [practica4.pkt](files/practica4.pkt)

## Topología de red:

La topología de nuestra red es de tipo <b>anillo</b>. Es claro ver que esta es nuestra topología por como están los Routers conectados, cada Router está conectado a otros dos Routers, uno de cada lado, formando así un anillo.

En la siguiente imagen podemos apreciar también las diferentes vLAN configuradas en la red:

| ![](img/red_anillo.png)
|:--------------------------------:|
| Topología tipo anillo de la red


## Tabla de los equipos


## Pruebas de conexión de los equipos en la red

### Para equipos en la red LAN

- `Laptop-Filos` a `Laptop-Psico`

    ```
	C:\>ping 192.168.20.1

	Pinging 192.168.20.1 with 32 bytes of data:

	Reply from 192.168.20.1: bytes=32 time<1ms TTL=126
	Reply from 192.168.20.1: bytes=32 time<1ms TTL=126
	Reply from 192.168.20.1: bytes=32 time<1ms TTL=126
	Reply from 192.168.20.1: bytes=32 time<1ms TTL=126

	Ping statistics for 192.168.20.1:
	    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
	Approximate round trip times in milli-seconds:
	    Minimum = 0ms, Maximum = 0ms, Average = 0ms
    ```
    
- `Laptop-Economia` a `Laptop-Psico`
    
    ```
	C:\>ping 192.168.20.1

	Pinging 192.168.20.1 with 32 bytes of data:

	Reply from 192.168.20.1: bytes=32 time<1ms TTL=126
	Reply from 192.168.20.1: bytes=32 time<1ms TTL=126
	Reply from 192.168.20.1: bytes=32 time<1ms TTL=126
	Reply from 192.168.20.1: bytes=32 time<1ms TTL=126

	Ping statistics for 192.168.20.1:
	    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
	Approximate round trip times in milli-seconds:
	    Minimum = 0ms, Maximum = 0ms, Average = 0ms
    
    ```
    
- `Laptop-Derecho` a `Laptop-Psico`

	```
	C:\>ping 192.168.20.1

	Pinging 192.168.20.1 with 32 bytes of data:

	Reply from 192.168.20.1: bytes=32 time<1ms TTL=125
	Reply from 192.168.20.1: bytes=32 time<1ms TTL=125
	Reply from 192.168.20.1: bytes=32 time<1ms TTL=125
	Reply from 192.168.20.1: bytes=32 time<1ms TTL=125

	Ping statistics for 192.168.20.1:
	    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
	Approximate round trip times in milli-seconds:
	    Minimum = 0ms, Maximum = 0ms, Average = 0ms
    ```
    
- `Laptop-Economia` a `Laptop-Filos`

	```
	C:\>ping 192.168.10.1

	Pinging 192.168.10.1 with 32 bytes of data:

	Reply from 192.168.10.1: bytes=32 time<1ms TTL=126
	Reply from 192.168.10.1: bytes=32 time<1ms TTL=126
	Reply from 192.168.10.1: bytes=32 time<1ms TTL=126
	Reply from 192.168.10.1: bytes=32 time<1ms TTL=126

	Ping statistics for 192.168.10.1:
	    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
	Approximate round trip times in milli-seconds:
	    Minimum = 0ms, Maximum = 0ms, Average = 0ms
	```
	
- `Laptop-Derecho` a `Laptop-Filos`

	```
	C:\>ping 192.168.10.1

	Pinging 192.168.10.1 with 32 bytes of data:

	Reply from 192.168.10.1: bytes=32 time<1ms TTL=126
	Reply from 192.168.10.1: bytes=32 time<1ms TTL=126
	Reply from 192.168.10.1: bytes=32 time<1ms TTL=126
	Reply from 192.168.10.1: bytes=32 time<1ms TTL=126

	Ping statistics for 192.168.10.1:
	    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
	Approximate round trip times in milli-seconds:
	    Minimum = 0ms, Maximum = 0ms, Average = 0ms
	```
	
- `Laptop-Derecho` a `Laptop-Economia`

	```
	C:\>ping 192.168.40.1

	Pinging 192.168.40.1 with 32 bytes of data:

	Reply from 192.168.40.1: bytes=32 time<1ms TTL=126
	Reply from 192.168.40.1: bytes=32 time<1ms TTL=126
	Reply from 192.168.40.1: bytes=32 time<1ms TTL=126
	Reply from 192.168.40.1: bytes=32 time<1ms TTL=126

	Ping statistics for 192.168.40.1:
	    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
	Approximate round trip times in milli-seconds:
	    Minimum = 0ms, Maximum = 0ms, Average = 0ms
    ```
### Para equipos a routers 

- `Laptop-Psico` a `Router-Psico GigabitEthernet0/0`
	
	```
	C:\>ping 192.168.20.254

	Pinging 192.168.20.254 with 32 bytes of data:

	Reply from 192.168.20.254: bytes=32 time<1ms TTL=255
	Reply from 192.168.20.254: bytes=32 time<1ms TTL=255
	Reply from 192.168.20.254: bytes=32 time<1ms TTL=255
	Reply from 192.168.20.254: bytes=32 time<1ms TTL=255

	Ping statistics for 192.168.20.254:
	    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
	Approximate round trip times in milli-seconds:
	    Minimum = 0ms, Maximum = 0ms, Average = 0ms
	```
	
- `Laptop-Psico` a `Router-Psico GigabitEthernet1/0`
	
	```
	C:\>ping 198.51.100.2

	Pinging 198.51.100.2 with 32 bytes of data:

	Reply from 198.51.100.2: bytes=32 time<1ms TTL=255
	Reply from 198.51.100.2: bytes=32 time<1ms TTL=255
	Reply from 198.51.100.2: bytes=32 time<1ms TTL=255
	Reply from 198.51.100.2: bytes=32 time<1ms TTL=255

	Ping statistics for 198.51.100.2:
	    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
	Approximate round trip times in milli-seconds:
	    Minimum = 0ms, Maximum = 0ms, Average = 0ms
	```
- `Laptop-Psico` a `Router-Psico GigabitEthernet2/0`
	
	```
	C:\>ping 198.51.100.13

	Pinging 198.51.100.13 with 32 bytes of data:

	Reply from 198.51.100.13: bytes=32 time<1ms TTL=255
	Reply from 198.51.100.13: bytes=32 time<1ms TTL=255
	Reply from 198.51.100.13: bytes=32 time<1ms TTL=255
	Reply from 198.51.100.13: bytes=32 time<1ms TTL=255

	Ping statistics for 198.51.100.13:
	    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
	Approximate round trip times in milli-seconds:
	    Minimum = 0ms, Maximum = 0ms, Average = 0ms
	```
	
- `Laptop-Psico` a `Router-Filos GigabitEthernet0/0`
	
	```
	C:\>ping 192.168.10.254

	Pinging 192.168.10.254 with 32 bytes of data:

	Reply from 192.168.10.254: bytes=32 time<1ms TTL=255
	Reply from 192.168.10.254: bytes=32 time<1ms TTL=255
	Reply from 192.168.10.254: bytes=32 time<1ms TTL=255
	Reply from 192.168.10.254: bytes=32 time<1ms TTL=255

	Ping statistics for 192.168.10.254:
	    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
	Approximate round trip times in milli-seconds:
	    Minimum = 0ms, Maximum = 0ms, Average = 0ms
	```	

- `Laptop-Psico` a `Router-Filos GigabitEthernet1/0`
	
	```
	C:\>ping 198.51.100.9

	Pinging 198.51.100.9 with 32 bytes of data:

	Reply from 198.51.100.9: bytes=32 time<1ms TTL=255
	Reply from 198.51.100.9: bytes=32 time<1ms TTL=255
	Reply from 198.51.100.9: bytes=32 time<1ms TTL=255
	Reply from 198.51.100.9: bytes=32 time<1ms TTL=255

	Ping statistics for 198.51.100.9:
	    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
	Approximate round trip times in milli-seconds:
	    Minimum = 0ms, Maximum = 0ms, Average = 0ms
	```
	
- `Laptop-Psico` a `Router-Filos GigabitEthernet2/0`
	
	```
	C:\>ping 198.51.100.14

	Pinging 198.51.100.14 with 32 bytes of data:

	Reply from 198.51.100.14: bytes=32 time<1ms TTL=255
	Reply from 198.51.100.14: bytes=32 time<1ms TTL=255
	Reply from 198.51.100.14: bytes=32 time<1ms TTL=255
	Reply from 198.51.100.14: bytes=32 time<1ms TTL=255

	Ping statistics for 198.51.100.14:
	    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
	Approximate round trip times in milli-seconds:
	    Minimum = 0ms, Maximum = 0ms, Average = 0ms
	```
	
- `Laptop-Psico` a `Router-Economia GigabitEthernet0/0`
	
	```
	C:\>ping 192.168.40.254

	Pinging 192.168.40.254 with 32 bytes of data:

	Reply from 192.168.40.254: bytes=32 time<1ms TTL=254
	Reply from 192.168.40.254: bytes=32 time<1ms TTL=254
	Reply from 192.168.40.254: bytes=32 time<1ms TTL=254
	Reply from 192.168.40.254: bytes=32 time=10ms TTL=254

	Ping statistics for 192.168.40.254:
	    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
	Approximate round trip times in milli-seconds:
	    Minimum = 0ms, Maximum = 10ms, Average = 2ms

	```
	
- `Laptop-Psico` a `Router-Economia GigabitEthernet1/0`
	
	```
	C:\>ping 198.51.100.1

	Pinging 198.51.100.1 with 32 bytes of data:

	Reply from 198.51.100.1: bytes=32 time<1ms TTL=254
	Reply from 198.51.100.1: bytes=32 time<1ms TTL=254
	Reply from 198.51.100.1: bytes=32 time<1ms TTL=254
	Reply from 198.51.100.1: bytes=32 time<1ms TTL=254

	Ping statistics for 198.51.100.1:
	    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
	Approximate round trip times in milli-seconds:
	    Minimum = 0ms, Maximum = 0ms, Average = 0ms
	```
	
- `Laptop-Psico` a `Router-Economia GigabitEthernet2/0`
	
	```
	C:\>ping 198.51.100.5

	Pinging 198.51.100.5 with 32 bytes of data:

	Reply from 198.51.100.5: bytes=32 time<1ms TTL=254
	Reply from 198.51.100.5: bytes=32 time<1ms TTL=254
	Reply from 198.51.100.5: bytes=32 time<1ms TTL=254
	Reply from 198.51.100.5: bytes=32 time<1ms TTL=254

	Ping statistics for 198.51.100.5:
	    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
	Approximate round trip times in milli-seconds:
	    Minimum = 0ms, Maximum = 0ms, Average = 0ms
	```
	
- `Laptop-Psico` a `Router-Derecho GigabitEthernet0/0`
	
	```
	C:\> ping 192.168.30.254

	Pinging 192.168.30.254 with 32 bytes of data:

	Reply from 192.168.30.254: bytes=32 time<1ms TTL=253
	Reply from 192.168.30.254: bytes=32 time<1ms TTL=253
	Reply from 192.168.30.254: bytes=32 time<1ms TTL=253
	Reply from 192.168.30.254: bytes=32 time<1ms TTL=253

	Ping statistics for 192.168.30.254:
	    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
	Approximate round trip times in milli-seconds:
	    Minimum = 0ms, Maximum = 0ms, Average = 0ms
	```
	
- `Laptop-Psico` a `Router-Derecho GigabitEthernet1/0`
	
	```
	C:\>ping 198.51.100.10

	Pinging 198.51.100.10 with 32 bytes of data:

	Reply from 198.51.100.10: bytes=32 time<1ms TTL=253
	Reply from 198.51.100.10: bytes=32 time<1ms TTL=253
	Reply from 198.51.100.10: bytes=32 time<1ms TTL=253
	Reply from 198.51.100.10: bytes=32 time<1ms TTL=253

	Ping statistics for 198.51.100.10:
	    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
	Approximate round trip times in milli-seconds:
	    Minimum = 0ms, Maximum = 0ms, Average = 0ms
    	```
    
- `Laptop-Psico` a `Router-Derecho GigabitEthernet2/0`
	
	```
    	C:\>ping 198.51.100.6
  
	Pinging 198.51.100.6 with 32 bytes of data:

	Reply from 198.51.100.6: bytes=32 time<1ms TTL=253
	Reply from 198.51.100.6: bytes=32 time<1ms TTL=253
	Reply from 198.51.100.6: bytes=32 time<1ms TTL=253
	Reply from 198.51.100.6: bytes=32 time<1ms TTL=253

	Ping statistics for 198.51.100.6:
	    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
	Approximate round trip times in milli-seconds:
	    Minimum = 0ms, Maximum = 0ms, Average = 0ms
	```    


## Configuración de los switches y routeadores 

Listamos los archivos `.txt` que guarda cada uno la salida del comando `show startup-config` para su respectivo switch o router:

1. Switches:
    * [Switch-Filos](files/Switch-Filos.txt)
    * [Switch-Psico](files/Switch-Psico.txt)
    * [Switch-Economia](files/Switch-Economia.txt)
    * [Switch-Derecho](files/Switch-Derecho.txt)

2. Routers:
    * [Router-Filos](files/Router-Filos.txt)
    * [Router-Psico](files/Router-Psico.txt)
    * [Router-Economia](files/Router-Economia.txt)
    * [Router-Derecho](files/Router-Derecho.txt)
