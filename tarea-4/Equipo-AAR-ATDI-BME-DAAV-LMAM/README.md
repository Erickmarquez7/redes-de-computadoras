# Equipo-AAR-ATDI-BME-DAAV-LMAM

| Integrante                     | Número de Cuenta | Usuario de GitLab   |
|:------------------------------:|:----------------:|:-------------------:|
| Acosta Arzate Rubén            | 317205776        | `rubenAcostaArzate` |
| Alvarado Torres David Ignacio  | 316167613        | `ddalt`             |
| Bernal Marquez Erick           | 317042522        | `Erickmarquez7`     |
| Deloya Andrade Ana Valeria     | 317277582        | `avdeloya13`        |
| López Miranda Angel Mauricio   | 317034808        | `MauricioLMiranda`  |

# [Tarea-4](https://redes-ciencias-unam.gitlab.io/2023-2/laboratorio/tarea-4/)


## Procedimiento

Primero revisamos que tengamos las herramientas instaladas en nuestro sistema, en el caso de linux ubutu

```
apt install wireshark
```

```
apt install tcpdump
```

```
apt install nmap
```

Estos comandos se encargan de instalar las herramientas necesarias utilizando el manejador de paquetes *apt*

## Dirección IP al servidor DHCP

### Renovamos IP
Desactivamos y volvemos a activar la configuración de la interfaz de red

```
ifdown "${IFACE}"
```
Desactiva la configuración

```
ifup "${IFACE}"
```
Activa la configuración

Donde *${IFACE}* es el nombre de nuestra interfaz de red

Desactivamos y volvemos a activar la conexión de red de Network Manager

```
nmcli connection down "${NAME}"
```
Desactiva la conexión

```
nmcli connection up "${NAME}"
```
Activa la conexión

Donde *${IFACE}* es el nombre de nuestra conexión de red

Solicitamos el servicio de DHCP

```
dhclient -r "${IFACE}"
```
Solicita el servicio DHCP

### Dirección local

Obtenemos dirección MAC e IP de la interfaz de red con cualquiera de los siguientes comandos

```
ifconfig -a
```
```
ip addr
```

Ambos comandos obtienen la dirección IP, solo que lo mustran de manera diferente

### Dirección del ruteador

Obtenemos la dirección del ruteador con cualquiera de los siguientes comandos

```
netstat -rn
```

```
route -n
```

```
ip route show
```

Los comandos obtienen la dirección IP, solo que lo mustran de manera diferente

### Dirección del servidor DNS

```
cat /etc/resolv.conf
```
Muestra el archivo resolv.conf

Este es un archivo resolv.conf dinámico para conectar clientes locales al sistema de resolución de stubs de DNS interno de systemd-resolved. Este archivo enumera todos los dominios de búsqueda configurados.

```
nmcli connection show "${NAME}" | grep -i DNS
```
Muestra las direcciónes IPv4 y/o IPv6 del servidor DNS para nuestra conexión de red de Network Manager

## Captura de trafico

## Pruebas de conectividad

