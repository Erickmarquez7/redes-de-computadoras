# Equipo-AAR-ATDI-BME-DAAV-LMAM

| Integrantes                    | Número de Cuenta | Usuario de GitLab   |
|:------------------------------:|:----------------:|:-------------------:|
| Acosta Arzate Rubén            | 317205776        | `rubenAcostaArzate` |
| Alvarado Torres David Ignacio  | 316167613        | `ddalt`             |
| Bernal Marquez Erick           | 317042522        | `Erickmarquez7`     |
| Deloya Andrade Ana Valeria     | 317277582        | `avdeloya13`        |
| López Miranda Angel Mauricio   | 317034808        | `MauricioLMiranda`  |

# [Practica-3](https://redes-ciencias-unam.gitlab.io/2023-2/laboratorio/practica-3/)

En este enlace se encuentra el archivo `.pkt` de la práctica: [practica3.pkt](files/practica3.pkt)

## Topología de red:

La topología utilizada es Estrella como podemos ver en la siguiente imagen

| ![](img/top.png)                 $$$$$$$$$$$$$Hay que cambiar la imagen, ya que eliminamos compus
|:-------------------------:|
| Topología estrella de la red

En la siguiente imágen podemos ver la totalidad de nuestra red, y podemos ver que tenemos un switch
en cada piso del edificio que estamos modelando. Los clientes están acomodados de tal forma que
sus cableados forman lo que parece ser una sola linea recta, pero en realidad todos están conectados
por separado al switch, con su propio cable, formando una topología estrella como la de la imagen de arriba.


## Tabla de los equipos en vLAN:

<table>
    <thead style="text-align: center;">
        <tr>
            <th>vLAN</th>
            <th>Grupo de equipos</th>
            <th>Equipo</th>
        </tr>
    </thead>
    <tbody style="text-align: center;">
        <tr>
            <td rowspan=6>vLAN 2</td>
            <td rowspan=6>Computadoras</td>
            <td>PC-P1-1</td>
        </tr>
       <tr>
            <td>PC-P1-2</td>
        </tr>
        <tr>
            <td>PC-P2-3</td>
        </tr>
        <tr>
            <td>PC-P2-4</td>
        </tr>
        <tr>
            <td>PC-P3-1</td>
        </tr>
        <tr>
            <td>PC-P3-6</td>
        </tr>
        <tr>
            <td rowspan=2>vLAN 3</td>
            <td rowspan=2>Impresoras</td>
            <td>Printer-P1-1</td>
        </tr>
       <tr>
            <td>Printer-P2-1</td>
        </tr>
        <tr>
            <td>vLAN 4</td>
            <td>Servidores</td>
            <td>Server-P1-1</td>
        </tr>
       <tr>
            <td rowspan=3>vLAN 100</td>
            <td rowspan=3>Impresoras</td>
            <td>Smartphone 1</td>
        </tr>
       <tr>
            <td>Tablet 1</td>
        </tr>
        <tr>
            <td>Tablet 2</td>
        </tr>    
    </tbody>
</table>


## Tabla de conexión

<table>
    <thead style="text-align: center;">
        <tr>
            <th>Hostname</th>
            <th>Conexión con otros switches</th>
            <th>Local Interface</th>
            <th>Neighbor Port ID</th>
        </tr>
    </thead>
    <tbody style="text-align: center;">
        <tr>
            <td>Switch-Access-P1</td>
            <td>SwitchDistro-P1</td>
            <td>Gig 0/1</td>
            <td>Gig 1/1</td>
        </tr>
       <tr>
            <td rowspan=2>SwitchDistro-P1</td>
            <td>Switch-Access-P1</td>
            <td>Gig 1/1</td>
            <td>Gig 0/1</td>
        </tr>
        <tr>
	        <td>Filos-Switch-Core</td>
	        <td>Gig 0/1</td>
	        <td>Fas 0/2</td>
        </tr>
	    <tr>
            <td>Switch-Access-P2</td>
            <td>SwitchDistro-P2</td>
            <td>Gig 0/1</td>
            <td>Gig 1/1</td>
        </tr>
       <tr>
            <td rowspan=2>SwitchDistro-P2</td>
            <td>Switch-Access-P2</td>
            <td>Gig 1/1</td>
            <td>Gig 0/1</td>
        </tr>
        <tr>
	        <td>Filos-Switch-Core</td>
	        <td>Gig 0/1</td>
	        <td>Fas 0/1</td>
        </tr>
        <tr>
            <td>Switch-Access-P3</td>
            <td>SwitchDistro-P3</td>
            <td>Gig 0/1</td>
            <td>Gig 1/1</td>
        </tr>
       <tr>
            <td rowspan=2>SwitchDistro-P3</td>
            <td>Switch-Access-P3</td>
            <td>Gig 1/1</td>
            <td>Gig 0/1</td>
        </tr>
        <tr>
	        <td>Filos-Switch-Core</td>
	        <td>Gig 0/1</td>
	        <td>Fas 0/3</td>
        </tr>
	    <tr>
            <td rowspan=3>Filos-Switch-Core</td>
            <td>SwitchDistro-P3</td>
            <td>Fas 0/3</td>
            <td>Gig 0/1</td>
        </tr>
        <tr>
            <td>SwitchDistro-P2</td>
            <td>Fas 0/1</td>
            <td>Gig 0/1</td>
        </tr>
         <tr>
            <td>SwitchDistro-P1</td>
            <td>Fas 0/2</td>
            <td>Gig 0/1</td>
        </tr>
    </tbody>
</table>


## Tabla de ip

<table>
    <thead style="text-align: center;">
        <tr>
            <th>Piso</th>
            <th>Equipo</th>
            <th>Dirección IP</th>
        </tr>
    </thead>
    <tbody style="text-align: center;">
        <tr>
            <td rowspan=4>Piso 1</td>
            <td>PC-P1-1</td>
            <td>192.168.2.11</td>
        </tr>
        <tr>
            <td>PC-P1-2</td>
            <td>192.168.2.12</td>
        </tr>
        <tr>
            <td>Printer-P1-1</td>
            <td>192.168.3.11</td>
        </tr>
        <tr>
	        <td>Server-P1-1</td>
            <td>192.168.4.11</td>
        </tr>
        <tr>
            <td rowspan=6>Piso 2</td>
            <td>PC-P2-3</td>
            <td>192.168.2.13</td>
        </tr>
        <tr>
            <td>PC-P2-4</td>
            <td>192.168.2.14</td>
        </tr>
        <tr>
            <td>Printer-P2-1</td>
            <td>192.168.3.12</td>
        </tr>
		<tr>
            <td>Smartphone1</td>
            <td>192.168.1.12</td>
        </tr>
        <tr>
            <td>Tablet1</td>
            <td>192.168.1.13</td>
        </tr>
        <tr>
            <td>Tablet2</td>
            <td>192.168.1.11</td>
        </tr>
        <tr>
            <td rowspan=2>Piso 3</td>
            <td>PC-P3-1</td>
            <td>192.168.2.15</td>
        </tr>
        <tr>
            <td>PC-P3-6</td>
            <td>192.168.2.16</td>
        </tr>
    </tbody>
</table>

## Tabla de ruteo
