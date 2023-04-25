# NFS

## DEBIAN

1. Instalar los paquetes de NFS en la máquina Debian:

```
root@debian-11:~# apt install nfs-kernel-server
```

![]

2. Configurar las opciones de exportación de NFS del servidor Debian, en el archivo `/etc/exports`

```
root@debian-11:~# nano /etc/exports
```

Agregamos la opciones de exportación para el directorio `/srv`. Queremos que cualquier cliente en el segmento de red de la interaz host-only
tenga acceso a dicho directorio compartido, por lo que especificamos que el rango de direcciones IP que pueden acceder a `/srv` es 
`192.168.56.0/24`:

```
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#

/srv             192.168.56.0/24(rw,sync,no_root_squash,no_subtree_check)
```

Esta línea de código indica que los clientes en el rango `192.168.56.0/24` podrá acceder al directorio `/srv` del sevidor Debian
con privilegios de root y que podrán leer y escribir en él. Las demás opciones --

3. Para que los cambios que hicimos se hagan disponibles a los clientes que se comunicarán al servidor (el cliente CentOS), 
debemos reiniciar el el servidor NFS:

```
root@debian-11:~# systemctl restart nfs-kernel-server
```

4. La salida del comando `showmount -e` nos muestra que el directorio `/srv` efectivamente está exportado en el servidor
```
root@debian-11:~# showmount -e
Export list for debian-11:
/srv             192.168.56.0/24
/home            192.168.56.6
/var/nfs/general 192.168.56.6
```

## CENTOS

1. Instalamos la paqueteria de NFS para poder confifugurar un cliente NFS en la máquina con CentOS:

```
[root@centos-9 ~]# yum install nfs-utils
```

2. Verificamos que el sistema de archivos está exportado con el comando `showmount`. La salida del mismo nos indica que el 
directorio `/srv` de la máquina Debian sí está exportado.

```
[root@centos-9 ~]# showmount -e 192.168.56.4
Export list for 192.168.56.4:
/srv             192.168.56.0/24
/home            192.168.56.6
/var/nfs/general 192.168.56.6
```

3. Ahora vamos a crear un directorio en nuestro cliente CentOS para montar el directorio exportado `/srv` de nuestro servidor Debian:

```
[root@centos-9 ~]# mkdir -p /nfs/srv
```

4. Montamos el directorio compartido `/srv` del servidor Debian en el directorio que acabamos de crear:

```
[root@centos-9 ~]# mount 192.168.56.4:/srv /nfs/srv
```

La salida del comando `df -h` nos muestra que nuestro directorio compartido efectivamente fue montado en nuestro cliente CentOS:

```
[root@centos-9 ~]# df -h
Filesystem           Size  Used Avail Use% Mounted on
devtmpfs             4.0M     0  4.0M   0% /dev
tmpfs                386M     0  386M   0% /dev/shm
tmpfs                155M  3.8M  151M   3% /run
/dev/mapper/cs-root  8.0G  2.8G  5.3G  35% /
/dev/sda1           1014M  216M  799M  22% /boot
tmpfs                 78M  8.0K   78M   1% /run/user/1000
192.168.56.4:/srv    8.9G  3.4G  5.1G  40% /nfs/srv
```

5. Montar el directorio `/srv` de Debian en el cliente CentOS de manera automática cuando este se inicialice:

Añadimos el directorio `/srv` del servidor Debian al archivo `/etc/fstab`, colocando la siguiente línea al final del mismo:

```
192.168.56.4:/srv               /nfs/srv      nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0
```

Con la instrucción `auto` aseguramos que el sistema de archivos será montado automáticamente durante el arranque de la máquina
con CentOS. 


```
#
# /etc/fstab
# Created by anaconda on Wed Feb 22 02:20:11 2023
#
# Accessible filesystems, by reference, are maintained under '/dev/disk/'.
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info.
#
# After editing this file, run 'systemctl daemon-reload' to update systemd
# units generated from this file.
#
/dev/mapper/cs-root     /                       xfs     defaults        0 0
UUID=2cc0630c-9d7c-4266-932e-b22ed0289899 /boot                   xfs     defaults        0 0
/dev/mapper/cs-swap     none                    swap    defaults        0 0

# Motaje del servicio NFS
192.168.56.4:/srv       /nfs/srv        nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0
```
