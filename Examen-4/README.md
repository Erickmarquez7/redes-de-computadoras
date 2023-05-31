# Equipo-AAR-ATDI-BME-DAAV-LMAM

| Integrante                     | Número de Cuenta | Usuario de GitLab   |
|:------------------------------:|:----------------:|:-------------------:|
| Acosta Arzate Rubén            | 317205776        | `rubenAcostaArzate` |
| Alvarado Torres David Ignacio  | 316167613        | `ddalt`             |
| Bernal Marquez Erick           | 317042522        | `Erickmarquez7`     |
| Deloya Andrade Ana Valeria     | 317277582        | `avdeloya13`        |
| López Miranda Angel Mauricio   | 317034808        | `MauricioLMiranda`  |


## Explicación del proceso de creación de las imagenes de contenedor

Antes de la creación nos aseguramos de que docker se haya instalado correctamente de la siguiente pagina https://www.docker.com/products/docker-desktop/ y probamos con el siguiente comando

```
usuario@laptop:~$ docker run -it hello-world
```
No debería mostrar error alguno

Una vez que nos hayamos asegurado de la correcta instalación iniciamos sessión con 

```
usuario@laptop:~$ docker login docker.io
```

Nos pedirá usuario y contraseña

Ahora sí, para la creación de la imagen hacemos un __dockerfile__ como se muestra en el siguiente archivo

[dockerfile](files/linux-doc/Dockerfile)

La explicación de lo qué hace viene en el mismo archivo

Construimos la imagen con __docker build__.

```
usuario@laptop:~$ TAG=[usuario]/[contenedor]
usuario@laptop:~$ docker build --progress plain -t "${TAG}" ./
```

Utilizamos __--progress plain__ para capturar la salida de __docker build__, la cual viene mostrada en la carpeta de _files_

Verificamos listando las imagenes del contenedor con

```
usuario@laptop:~$ docker images
REPOSITORY           TAG           IMAGE ID       CREATED          SIZE
erick954/linux-doc   latest        98a60d1391f0   54 minutes ago   188MB
```

También podemos utilizar ejecutar la imagen para comprobar que se haya hecho correctamente

```
usuario@laptop:~$ docker run -it -p 8080:80 erick954/linux-doc:latest
```

Veamos que en efecto funciona y corresponde localhost:8080

| ![](img/linux-doc.png)
|:-------------------------:|
| Pagina de la documentación de linux


Por ultimo enviamos las imagenes al __registry__

```
usuario@laptop:~$ TAG=[usuario]/[contenedor]
usuario@laptop:~$ docker push "${TAG}"
```

Y notamos que en nuestra sessión de docker se muestran las imagenes

| ![](img/docker-imagen.png)
|:-------------------------:|
| Sessión con la imagen correspondiente

## Explicación del proceso de instalación de k3s en Debian 11

Antes de la instalación debemos preparar la maquina liberando memoria RAM, esto puede ser de varias maneras por lo que lo dejaremos a consideración del usuario. Además de deshabilitar los servicios de apache de la entrega anterior.

Establecemos un área de intercambio _swap_ para que los nodos consuman menos memoria RAM

Habilitamos la politica de _swap_ en el archivo de configuración /etc/sysctl.d/local.conf

```
root@example:~# cat >> /etc/sysctl.d/local.conf << EOF
###################################################################
# https://www.kernel.org/doc/html/latest/admin-guide/sysctl/vm.html#swappiness
vm.swappiness = 1
EOF
```

Recargamos la configuración

```
root@example:~# sysctl -p

root@example:~# sysctl -p /etc/sysctl.d/local.conf
vm.swappiness = 1

root@example:~# cat /proc/sys/vm/swappiness
1
```

Creamos el archivo _./swap_ y le damos los permisos necesarios, además del archivo _sparse_ para SWAP

```
root@example:~# touch /.swap

root@example:~# chmod -c 0600 /.swap
mode of '/.swap' changed from 0644 (rw-r--r--) to 0600 (rw-------)

root@example:~# dd if=/dev/zero of=/.swap bs=1M count=1024 status=progress
1051721728 bytes (1.1 GB, 1003 MiB) copied, 17 s, 61.8 MB/s
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB, 1.0 GiB) copied, 18.6303 s, 57.6 MB/s

root@example:~# ls -lah /.swap
-rw------- 1 root root 1.0G May 22 12:56 /.swap
```

Creamos el área de intercambio

```
root@example:~# mkswap -L swap /.swap
Setting up swapspace version 1, size = 1024 MiB (1073737728 bytes)
LABEL=swap, UUID=6298196b-9e0e-4440-b41b-367e0b671f91
```

Por último verficamos y habilitamos el montaje swap

```
root@example:~# cat /etc/fstab
# /etc/fstab: static file system information
UUID=c0db73f0-f7cd-43df-b16e-20ae1caca357 / ext4 rw,discard,errors=remount-ro,x-systemd.growfs 0 1
UUID=ECD7-6DBA /boot/efi vfat defaults 0 0
/dev/disk/cloud/azure_resource-part1    /mnt    auto    defaults,nofail,comment=cloudconfig 0   2

# swap
/.swap  none    swap    defaults    0   0   ⬅️

root@example:~# swapon -va
swapon: /.swap: found signature [pagesize=4096, signature=swap]
swapon: /.swap: pagesize=4096, swapsize=1073741824, devsize=1073741824
swapon /.swap
```

Para k3s descargamos y cambiamos permisos del script de instalación

```
root@example:~# wget -c -nv -O ~/get-k3s-io.sh 'https://get.k3s.io/'
2023-05-22 13:04:24 URL:https://get.k3s.io/ [30463/30463] -> "/root/get-k3s-io.sh" [1]

root@example:~# chmod -c +x ./get-k3s-io.sh
mode of './get-k3s-io.sh' changed from 0644 (rw-r--r--) to 0755 (rwxr-xr-x)
```

Definimos variables de entorno para personalización de la instalación de 3ks

```
root@example:~# export INSTALL_K3S_SKIP_START="true"
root@example:~# export INSTALL_K3S_EXEC="--tls-san='k3s.[dominio.com]' --tls-san='[mi.ip.publica.x]' --disable-cloud-controller --disable=metrics-server --disable=servicelb --disable=traefik"
root@example:~# ~/get-k3s-io.sh
[INFO]  Finding release for channel stable
[INFO]  Using v1.26.4+k3s1 as release
[INFO]  Downloading hash https://github.com/k3s-io/k3s/releases/download/v1.26.4+k3s1/sha256sum-amd64.txt
[INFO]  Downloading binary https://github.com/k3s-io/k3s/releases/download/v1.26.4+k3s1/k3s
[INFO]  Verifying binary download
[INFO]  Installing k3s to /usr/local/bin/k3s
[INFO]  Finding available k3s-selinux versions
/root/get-k3s-io.sh: 407: [: k3s-selinux-1.2-2.el8.noarch.rpm: unexpected operator
[INFO]  Creating /usr/local/bin/kubectl symlink to k3s
[INFO]  Creating /usr/local/bin/crictl symlink to k3s
[INFO]  Creating /usr/local/bin/ctr symlink to k3s
[INFO]  Creating killall script /usr/local/bin/k3s-killall.sh
[INFO]  Creating uninstall script /usr/local/bin/k3s-uninstall.sh
[INFO]  env: Creating environment file /etc/systemd/system/k3s.service.env
[INFO]  systemd: Creating service file /etc/systemd/system/k3s.service
[INFO]  systemd: Enabling k3s unit
Created symlink /etc/systemd/system/multi-user.target.wants/k3s.service → /etc/systemd/system/k3s.service.
```

Reiniciamos el equipo y verificamos que k3s se haya iniciado de manera correcta

```
root@waningnew:~# PAGER=cat systemctl status --full k3s
root@waningnew:~# PAGER=cat systemctl status --full k3s
● k3s.service - Lightweight Kubernetes
     Loaded: loaded (/etc/systemd/system/k3s.service; enabled; vendor preset: enabled)
     Active: active (running) since Wed 2023-05-31 13:27:01 CST; 5min ago
       Docs: https://k3s.io
   Main PID: 642 (k3s-server)
      Tasks: 47
     Memory: 276.3M
        CPU: 30.550s
     CGroup: /system.slice/k3s.service
             ├─ 642 /usr/local/bin/k3s server
             ├─ 742 containerd
             ├─1323 /var/lib/rancher/k3s/data/163665c44bcc8e97514aeb518069c3c55e5ad6226d4ebf3c6d89cbd4057b6809/bin/containerd-shim-runc-v2 -namespace k8s.io -id f325fb4e869d0cee422c83a8a1ee66dd72678ad6c24d2d14475f0ad1b9627e17 -address /run/k3s/containerd/containerd.sock
             └─1324 /var/lib/rancher/k3s/data/163665c44bcc8e97514aeb518069c3c55e5ad6226d4ebf3c6d89cbd4057b6809/bin/containerd-shim-runc-v2 -namespace k8s.io -id ec94db935d60321e21cc36c3721f00ffe83aa49b723fe7daf900f7dc7ea15b65 -address /run/k3s/containerd/containerd.sock
```

Revisamos que el puerto 6443 correspondiente a la API de Kubernetes se escucha

```
root@example:~# netstat -ntulp | grep 6443
tcp6       0      0 :::6443           :::*            LISTEN      642/k3s server
```

Preparamos el archivo _~/.kube/config_ y le cambiamos los permisos necesarios

```
root@example:~# adduser redes staff
Añadiendo al usuario `redes' al grupo `staff' ...
Añadiendo al usuario redes al grupo staff
Hecho.

root@example:~# chown -c root:staff /etc/rancher/k3s/k3s.yaml
cambiado el propietario de '/etc/rancher/k3s/k3s.yaml' de root:root a root:staff

root@example:~# chmod -c 0440 /etc/rancher/k3s/k3s.yaml
el modo de '/etc/rancher/k3s/k3s.yaml' cambia de 0600 (rw-------) a 0440 (r--r-----)
```

Hacemos liga simbólica a _3ks.yaml_

```
root@waningnew:~# mkdir -vp ~/.kube
mkdir: se ha creado el directorio '/root/.kube'
root@waningnew:~# ln -vsf /etc/rancher/k3s/k3s.yaml ~/.kube/config
'/root/.kube/config' -> '/etc/rancher/k3s/k3s.yaml'
root@waningnew:~# ls -la ~/.kube
total 8
drwxr-xr-x  2 root root 4096 may 31 13:40 .
drwx------ 10 root root 4096 may 31 13:40 ..
lrwxrwxrwx  1 root root   25 may 31 13:40 config -> /etc/rancher/k3s/k3s.yaml
```

Copimos el archivo _k3s.yaml_ en la ruta _~/.kube/config_ con el usuario redes y ajustamos los permisos

```
root@example:~# su - redes

redes@example:~$ mkdir -vp ~/.kube
mkdir: se ha creado el directorio '/home/redes/.kube'

redes@example:~$ sudo cp -v /etc/rancher/k3s/k3s.yaml ~/.kube/config
'/etc/rancher/k3s/k3s.yaml' -> '/home/redes/.kube/config'

redes@example:~$ sudo chown -cR redes:staff ~/.kube
cambiado el propietario de '/home/redes/.kube/config' de root:root a redes:staff
cambiado el propietario de '/home/redes/.kube' de redes:redes a redes:staff

redes@example:~$ chmod -c 0640 ~/.kube/config
el modo de '/home/redes/.kube/config' cambia de 0440 (r--r-----) a 0640 (rw-r-----)

redes@example:~$ ls -la ~/.kube
total 12
drwxr-xr-x 2 redes staff 4096 may 31 13:41 .
drwxr-xr-x 8 redes redes 4096 may 31 13:41 ..
-rw-r----- 1 redes staff 2961 may 31 13:41 config
```

Nos conectamos al cluster de Kubernetes

```
redes@example:~$ kubectl version --short
Flag --short has been deprecated, and will be removed in the future. The --short output will become the default.
Client Version: v1.26.5+k3s1
Kustomize Version: v4.5.7
Server Version: v1.26.5+k3s1
redes@example:~$ kubectl get nodes -o wide
NAME           STATUS   ROLES                  AGE   VERSION        INTERNAL-IP   EXTERNAL-IP   OS-IMAGE                         KERNEL-VERSION          CONTAINER-RUNTIME
waningnew.me   Ready    control-plane,master   15m   v1.26.5+k3s1   10.0.0.4      <none>        Debian GNU/Linux 11 (bullseye)   5.10.0-23-cloud-amd64   containerd://1.7.1-k3s1
```

Abrimos el puerto 6443 en azure en el grupo de seguridad con el nombre de _kube-api-server_

| ![](img/azure-puerto.jpg)
|:-------------------------:|
| Portal de Azure

## Explicación del proceso de instalación del ingress controller en el cluster

## Explicación del proceso de despliegue de los sitios web en el cluster de Kubernetes

## Explicación de la configuración de SSL/TLS en el ingress controlle