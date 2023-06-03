# Laboratorio virtual de redes

 Erick Bernal Márquez
   - Número de cuenta: `317042522`
   - Usuario de GitLab: `@Erickmarquez7`

## Debian 11

### Información del sistema

```bash
erickdebi@debian-11:~$ neofetch
       _,met$$$$$gg.          erickdebi@debian-11
    ,g$$$$$$$$$$$$$$$P.       -------------------
  ,g$$P"       "Y$$.".        OS: Debian GNU/Linux 11 (bullseye) x86_64
 ,$$P'              `$$$.     Host: VirtualBox 1.2
',$$P       ,ggs.     `$$b:   Kernel: 5.10.0-21-amd64
`d$$'     ,$P"'   .    $$$    Uptime: 7 mins
 $$P      d$'     ,    $$P    Packages: 680 (dpkg)
 $$:      $$.   -    ,d$$'    Shell: bash 5.1.4
 $$;      Y$b._   _,d$P'      Resolution: preferred
 Y$$.    `.`"Y$$$$P"'         Terminal: /dev/pts/0
 `$$b      "-.__              CPU: AMD Ryzen 3 3250U with Radeon Graphics (1) @ 2.595GHz
  `Y$$                        GPU: 00:02.0 VMware SVGA II Adapter
   `Y$$.                      Memory: 72MiB / 976MiB
     `$$b.
       `Y$$b.
          `"Y$b._
              `


erickdebi@debian-11:~$ uname -a
Linux debian-11 5.10.0-21-amd64 #1 SMP Debian 5.10.162-1 (2023-01-21) x86_64 GNU/Linux


erickdebi@debian-11:~$ cat /etc/os-release
PRETTY_NAME="Debian GNU/Linux 11 (bullseye)"
NAME="Debian GNU/Linux"
VERSION_ID="11"
VERSION="11 (bullseye)"
VERSION_CODENAME=bullseye
ID=debian
HOME_URL="https://www.debian.org/"
SUPPORT_URL="https://www.debian.org/support"
BUG_REPORT_URL="https://bugs.debian.org/"


erickdebi@debian-11:~$ cat /etc/debian_version
11.6


erickdebi@debian-11:~$ lsmod
Module                  Size  Used by
vboxvideo              49152  0
ghash_clmulni_intel    16384  0
aesni_intel           372736  0
vmwgfx                385024  2
snd_intel8x0           49152  0
libaes                 16384  1 aesni_intel
crypto_simd            16384  1 aesni_intel
snd_ac97_codec        180224  1 snd_intel8x0
cryptd                 24576  2 crypto_simd,ghash_clmulni_intel
glue_helper            16384  1 aesni_intel
rapl                   20480  0
ac97_bus               16384  1 snd_ac97_codec
ttm                   114688  2 vmwgfx,vboxvideo
snd_pcm               143360  2 snd_intel8x0,snd_ac97_codec
pcspkr                 16384  0
serio_raw              20480  0
joydev                 28672  0
drm_kms_helper        278528  2 vmwgfx,vboxvideo
snd_timer              49152  1 snd_pcm
vboxguest             450560  2
snd                   110592  4 snd_intel8x0,snd_timer,snd_ac97_codec,snd_pcm
sg                     36864  0
soundcore              16384  1 snd
cec                    61440  1 drm_kms_helper
evdev                  28672  3
ac                     16384  0
button                 24576  0
nfnetlink              20480  0
drm                   626688  6 vmwgfx,drm_kms_helper,vboxvideo,ttm
fuse                  167936  1
configfs               57344  1
ip_tables              36864  0
x_tables               53248  1 ip_tables
autofs4                53248  2
ext4                  942080  1
crc16                  16384  1 ext4
mbcache                16384  1 ext4
jbd2                  151552  1 ext4
crc32c_generic         16384  0
hid_generic            16384  0
usbhid                 65536  0
hid                   151552  2 usbhid,hid_generic
sr_mod                 28672  0
sd_mod                 61440  3
t10_pi                 16384  1 sd_mod
crc_t10dif             20480  1 t10_pi
cdrom                  73728  1 sr_mod
crct10dif_generic      16384  0
ata_generic            16384  0
ahci                   40960  2
ata_piix               36864  0
ohci_pci               20480  0
libahci                45056  1 ahci
ohci_hcd               61440  1 ohci_pci
ehci_pci               20480  0
libata                299008  4 ata_piix,libahci,ahci,ata_generic
ehci_hcd               98304  1 ehci_pci
crct10dif_pclmul       16384  1
crct10dif_common       16384  3 crct10dif_generic,crc_t10dif,crct10dif_pclmul
crc32_pclmul           16384  0
usbcore               331776  5 ohci_hcd,ehci_pci,usbhid,ehci_hcd,ohci_pci
psmouse               184320  0
crc32c_intel           24576  2
scsi_mod              270336  4 sd_mod,libata,sg,sr_mod
e1000                 163840  0
i2c_piix4              28672  0
usb_common             16384  3 ohci_hcd,usbcore,ehci_hcd
battery                24576  0
video                  61440  0


erickdebi@debian-11:~$ ps afx
    PID TTY      STAT   TIME COMMAND
      2 ?        S      0:00 [kthreadd]
      3 ?        I<     0:00  \_ [rcu_gp]
      4 ?        I<     0:00  \_ [rcu_par_gp]
      6 ?        I<     0:00  \_ [kworker/0:0H-events_highpri]
      7 ?        I      0:00  \_ [kworker/u2:0-flush-8:0]
      8 ?        I<     0:00  \_ [mm_percpu_wq]
      9 ?        S      0:00  \_ [rcu_tasks_rude_]
     10 ?        S      0:00  \_ [rcu_tasks_trace]
     11 ?        S      0:00  \_ [ksoftirqd/0]
     12 ?        I      0:00  \_ [rcu_sched]
     13 ?        S      0:00  \_ [migration/0]
     15 ?        S      0:00  \_ [cpuhp/0]
     17 ?        S      0:00  \_ [kdevtmpfs]
     18 ?        I<     0:00  \_ [netns]
     19 ?        S      0:00  \_ [kauditd]
     20 ?        S      0:00  \_ [khungtaskd]
     21 ?        S      0:00  \_ [oom_reaper]
     22 ?        I<     0:00  \_ [writeback]
     23 ?        S      0:00  \_ [kcompactd0]
     24 ?        SN     0:00  \_ [ksmd]
     25 ?        SN     0:00  \_ [khugepaged]
     43 ?        I<     0:00  \_ [kintegrityd]
     44 ?        I<     0:00  \_ [kblockd]
     45 ?        I<     0:00  \_ [blkcg_punt_bio]
     46 ?        I<     0:00  \_ [edac-poller]
     47 ?        I<     0:00  \_ [devfreq_wq]
     48 ?        I<     0:00  \_ [kworker/0:1H-kblockd]
     50 ?        I      0:00  \_ [kworker/0:2-ata_sff]
     51 ?        S      0:00  \_ [kswapd0]
     52 ?        I<     0:00  \_ [kthrotld]
     53 ?        I<     0:00  \_ [acpi_thermal_pm]
     54 ?        I<     0:00  \_ [ipv6_addrconf]
     55 ?        I      0:00  \_ [kworker/u2:1-ext4-rsv-conversion]
     64 ?        I<     0:00  \_ [kstrp]
     67 ?        I<     0:00  \_ [zswap-shrink]
     68 ?        I<     0:00  \_ [kworker/u3:0]
    105 ?        I<     0:00  \_ [ata_sff]
    106 ?        S      0:00  \_ [scsi_eh_0]
    107 ?        I<     0:00  \_ [scsi_tmf_0]
    108 ?        S      0:00  \_ [scsi_eh_1]
    109 ?        I<     0:00  \_ [scsi_tmf_1]
    110 ?        I      0:00  \_ [kworker/u2:2-events_unbound]
    111 ?        S      0:00  \_ [scsi_eh_2]
    112 ?        I<     0:00  \_ [scsi_tmf_2]
    113 ?        I      0:00  \_ [kworker/u2:3]
    114 ?        I      0:00  \_ [kworker/0:3-events_power_efficient]
    147 ?        S      0:00  \_ [jbd2/sda1-8]
    148 ?        I<     0:00  \_ [ext4-rsv-conver]
    257 ?        I<     0:00  \_ [iprt-VBoxWQueue]
    260 ?        I<     0:00  \_ [cryptd]
    263 ?        S      0:00  \_ [irq/18-vmwgfx]
    266 ?        I<     0:00  \_ [ttm_swap]
    268 ?        S      0:00  \_ [card0-crtc0]
    270 ?        S      0:00  \_ [card0-crtc1]
    272 ?        S      0:00  \_ [card0-crtc2]
    275 ?        S      0:00  \_ [card0-crtc3]
    276 ?        S      0:00  \_ [card0-crtc4]
    277 ?        S      0:00  \_ [card0-crtc5]
    281 ?        S      0:00  \_ [card0-crtc6]
    283 ?        S      0:00  \_ [card0-crtc7]
    725 ?        I      0:00  \_ [kworker/0:0-ata_sff]
      1 ?        Ss     0:01 /sbin/init
    184 ?        Ss     0:00 /lib/systemd/systemd-journald
    204 ?        Ss     0:00 /lib/systemd/systemd-udevd
    303 ?        Ss     0:00 /usr/sbin/cron -f
    312 ?        Ss     0:00 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
    328 ?        Ssl    0:00 /usr/sbin/rsyslogd -n -iNONE
    342 ?        Ss     0:00 /lib/systemd/systemd-logind
    350 ?        Ss     0:00 /sbin/wpa_supplicant -u -s -O /run/wpa_supplicant
    427 ?        Ssl    0:00 /sbin/dhclient -4 -v -i -pf /run/dhclient.enp0s3.pid -lf /var/lib/dhcp/dhclient.enp0s3.leases -I -df /var/lib/dhcp/dhclie
    490 ?        Ssl    0:00 /sbin/dhclient -4 -v -i -pf /run/dhclient.enp0s8.pid -lf /var/lib/dhcp/dhclient.enp0s8.leases -I -df /var/lib/dhcp/dhclie
    615 ?        Sl     0:00 /usr/bin/VBoxDRMClient
    619 ?        Sl     0:00 /usr/sbin/VBoxService --pidfile /var/run/vboxadd-service.sh
    679 tty1     Ss+    0:00 /sbin/agetty -o -p -- \u --noclear tty1 linux
    680 ?        Ss     0:00 sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups
    684 ?        Ss     0:00  \_ sshd: erickdebi [priv]
    706 ?        S      0:00      \_ sshd: erickdebi@pts/0
    707 pts/0    Ss     0:00          \_ -bash
    733 pts/0    R+     0:00              \_ ps afx
    687 ?        Ss     0:00 /lib/systemd/systemd --user
    688 ?        S      0:00  \_ (sd-pam)


erickdebi@debian-11:~$ hostname -I
10.0.2.15 192.168.56.101


erickdebi@debian-11:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:59:8d:01 brd ff:ff:ff:ff:ff:ff
    altname enp0s3
    inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic enp0s3
       valid_lft 86048sec preferred_lft 86048sec
    inet6 fe80::a00:27ff:fe59:8d01/64 scope link
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:5e:2a:b3 brd ff:ff:ff:ff:ff:ff
    altname enp0s8
    inet 192.168.56.101/24 brd 192.168.56.255 scope global dynamic enp0s8
       valid_lft 510sec preferred_lft 510sec
    inet6 fe80::a00:27ff:fe5e:2ab3/64 scope link
       valid_lft forever preferred_lft forever


erickdebi@debian-11:~$ ip route show
default via 10.0.2.2 dev eth0
10.0.2.0/24 dev eth0 proto kernel scope link src 10.0.2.15
169.254.0.0/16 dev eth0 scope link metric 1000
192.168.56.0/24 dev eth1 proto kernel scope link src 192.168.56.101


erickdebi@debian-11:~$ cat /etc/resolv.conf
nameserver 10.0.2.3


erickdebi@debian-11:~$ netstat -ntulp
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -
tcp6       0      0 :::22                   :::*                    LISTEN      -
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -


erickdebi@debian-11:~$ ping -c 4 1.1.1.1
PING 1.1.1.1 (1.1.1.1): 56 data bytes
64 bytes from 1.1.1.1: icmp_seq=0 ttl=63 time=99.169 ms
64 bytes from 1.1.1.1: icmp_seq=1 ttl=63 time=115.349 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=63 time=241.560 ms
64 bytes from 1.1.1.1: icmp_seq=3 ttl=63 time=161.180 ms
--- 1.1.1.1 ping statistics ---
4 packets transmitted, 4 packets received, 0% packet loss
round-trip min/avg/max/stddev = 99.169/154.315/241.560/55.268 ms
erickdebi@debian-11:~$ dig example.com.

; <<>> DiG 9.16.37-Debian <<>> example.com.
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 60238
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;example.com.			IN	A

;; ANSWER SECTION:
example.com.		9784	IN	A	93.184.216.34

;; Query time: 40 msec
;; SERVER: 10.0.2.3#53(10.0.2.3)
;; WHEN: Tue Feb 21 19:17:00 CST 2023
;; MSG SIZE  rcvd: 56
```

### Privilegios

```bash
erickdebi@debian-11:~$ getent passwd ${USER}
erickdebi:x:1000:1000:erickdebi,,,:/home/erickdebi:/bin/bash


erickdebi@debian-11:~$ id
uid=1000(erickdebi) gid=1000(erickdebi) groups=1000(erickdebi),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),44(video),46(plugdev),108(netdev),112(bluetooth),1001(wireshark)


erickdebi@debian-11:~$ groups
erickdebi cdrom floppy sudo audio dip video plugdev netdev bluetooth wireshark


erickdebi@debian-11:~$ sudo -l
Matching Defaults entries for erickdebi on debian-11:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User erickdebi may run the following commands on debian-11:
    (ALL : ALL) NOPASSWD: ALL


erickdebi@debian-11:~$ sudo -i
root@debian-11:~#
```

### Ubicación de herramientas

```bash
erickdebi@debian-11:~$ which wireshark tcpdump nmap netcat-openbsd ngrep dsniff wget curl whois dnsutils net-tools iproute2 iptables iptables-persistent tsocks inetutils-ping inetutils-traceroute inetutils-tools ethtool
/usr/bin/wireshark
/usr/bin/tcpdump
/usr/bin/nmap
/usr/bin/ngrep
/usr/bin/wget
/usr/bin/curl
/usr/bin/whois
/usr/bin/tsocks
/usr/bin/inetutils-traceroute


erickdebi@debian-11:~$ whereis wireshark tcpdump nmap netcat-openbsd ngrep dsniff wget curl whois dnsutils net-tools iproute2 iptables iptables-persistent tsocks inetutils-ping inetutils-traceroute inetutils-tools ethtool
wireshark: /usr/bin/wireshark /usr/lib/x86_64-linux-gnu/wireshark /etc/wireshark /usr/share/wireshark /usr/share/man/man1/wireshark.1.gz
tcpdump: /usr/bin/tcpdump /usr/share/man/man8/tcpdump.8.gz
nmap: /usr/bin/nmap /usr/share/nmap /usr/share/man/man1/nmap.1.gz
netcat-openbsd:
ngrep: /usr/bin/ngrep /usr/share/man/man8/ngrep.8.gz
dsniff: /usr/sbin/dsniff /usr/share/dsniff /usr/share/man/man8/dsniff.8.gz
wget: /usr/bin/wget /usr/share/man/man1/wget.1.gz /usr/share/info/wget.info.gz
curl: /usr/bin/curl /usr/share/man/man1/curl.1.gz
whois: /usr/bin/whois /usr/share/man/man1/whois.1.gz
dnsutils:
net-tools:
iproute2: /etc/iproute2 /usr/include/iproute2
iptables: /usr/sbin/iptables /etc/iptables /usr/share/iptables /usr/share/man/man8/iptables.8.gz
iptables-persistent:
tsocks: /usr/bin/tsocks /etc/tsocks.conf /usr/share/man/man8/tsocks.8.gz /usr/share/man/man1/tsocks.1.gz
inetutils-ping:
inetutils-traceroute: /usr/bin/inetutils-traceroute /usr/share/man/man1/inetutils-traceroute.1.gz
inetutils-tools:
ethtool: /usr/sbin/ethtool /usr/share/man/man8/ethtool.8.gz
```

## CentOS Stream 9

### Información del sistema

```bash
[root@localhost cdrom0]# neofetch
                 ..                    root@localhost
               .PLTJ.                  --------------
              <><><><>                 OS: CentOS Stream 9 x86_64
     KKSSV' 4KKK LJ KKKL.'VSSKK        Host: VirtualBox 1.2
     KKV' 4KKKKK LJ KKKKAL 'VKK        Kernel: 5.14.0-267.el9.x86_64
     V' ' 'VKKKK LJ KKKKV' ' 'V        Uptime: 14 mins
     .4MA.' 'VKK LJ KKV' '.4Mb.        Packages: 809 (rpm)
   . KKKKKA.' 'V LJ V' '.4KKKKK .      Shell: bash 5.1.8
 .4D KKKKKKKA.'' LJ ''.4KKKKKKK FA.    Resolution: 800x600
<QDD ++++++++++++  ++++++++++++ GFD>   CPU: AMD Ryzen 3 3250U with Radeon Graphics (1) @ 2.595GHz
 'VD KKKKKKKK'.. LJ ..'KKKKKKKK FV     GPU: 00:02.0 VMware SVGA II Adapter
   ' VKKKKK'. .4 LJ K. .'KKKKKV '      Memory: 206MiB / 771MiB
      'VK'. .4KK LJ KKA. .'KV'
     A. . .4KKKK LJ KKKKA. . .4
     KKA. 'KKKKK LJ KKKKK' .4KK
     KKSSA. VKKK LJ KKKV .4SSKK
              <><><><>
               'MKKM'
                 ''


[root@localhost cdrom0]# uname -a
Linux localhost.localdomain 5.14.0-267.el9.x86_64 #1 SMP PREEMPT_DYNAMIC Tue Feb 14 00:19:32 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux


[root@localhost cdrom0]# cat /etc/os-release
NAME="CentOS Stream"
VERSION="9"
ID="centos"
ID_LIKE="rhel fedora"
VERSION_ID="9"
PLATFORM_ID="platform:el9"
PRETTY_NAME="CentOS Stream 9"
ANSI_COLOR="0;31"
LOGO="fedora-logo-icon"
CPE_NAME="cpe:/o:centos:centos:9"
HOME_URL="https://centos.org/"
BUG_REPORT_URL="https://bugzilla.redhat.com/"
REDHAT_SUPPORT_PRODUCT="Red Hat Enterprise Linux 9"
REDHAT_SUPPORT_PRODUCT_VERSION="CentOS Stream"


[root@localhost cdrom0]# cat /etc/redhat-release
CentOS Stream release 9


[root@localhost cdrom0]# lsmod
Module                  Size  Used by
nls_utf8               16384  1
isofs                  61440  1
nft_fib_inet           16384  1
nft_fib_ipv4           16384  1 nft_fib_inet
nft_fib_ipv6           16384  1 nft_fib_inet
nft_fib                16384  3 nft_fib_ipv6,nft_fib_ipv4,nft_fib_inet
nft_reject_inet        16384  6
nf_reject_ipv4         16384  1 nft_reject_inet
nf_reject_ipv6         20480  1 nft_reject_inet
nft_reject             16384  1 nft_reject_inet
nft_ct                 24576  10
nft_chain_nat          16384  3
nf_nat                 57344  1 nft_chain_nat
nf_conntrack          188416  2 nf_nat,nft_ct
nf_defrag_ipv6         24576  1 nf_conntrack
nf_defrag_ipv4         16384  1 nf_conntrack
rfkill                 36864  1
ip_set                 61440  0
nf_tables             274432  210 nft_ct,nft_reject_inet,nft_fib_ipv6,nft_fib_ipv4,nft_chain_nat,nft_reject,nft_fib,nft_fib_inet
nfnetlink              20480  3 nf_tables,ip_set
snd_intel8x0           49152  0
snd_ac97_codec        176128  1 snd_intel8x0
vmwgfx                393216  2
ac97_bus               16384  1 snd_ac97_codec
snd_seq                94208  0
snd_seq_device         16384  1 snd_seq
snd_pcm               151552  2 snd_intel8x0,snd_ac97_codec
drm_ttm_helper         16384  1 vmwgfx
ttm                    90112  2 vmwgfx,drm_ttm_helper
drm_kms_helper        192512  1 vmwgfx
snd_timer              49152  2 snd_seq,snd_pcm
intel_rapl_msr         20480  0
intel_rapl_common      32768  1 intel_rapl_msr
snd                   122880  6 snd_seq,snd_seq_device,snd_intel8x0,snd_timer,snd_ac97_codec,snd_pcm
pcspkr                 16384  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
i2c_piix4              28672  0
sysimgblt              16384  1 drm_kms_helper
soundcore              16384  1 snd
fb_sys_fops            16384  1 drm_kms_helper
joydev                 28672  0
drm                   581632  6 vmwgfx,drm_kms_helper,drm_ttm_helper,ttm
fuse                  176128  1
xfs                  2048000  2
libcrc32c              16384  4 nf_conntrack,nf_nat,nf_tables,xfs
sr_mod                 28672  1
sd_mod                 69632  3
cdrom                  81920  2 isofs,sr_mod
t10_pi                 16384  1 sd_mod
sg                     49152  0
ata_generic            16384  0
ahci                   49152  2
ata_piix               45056  1
libahci                53248  1 ahci
libata                425984  4 ata_piix,libahci,ahci,ata_generic
e1000                 176128  0
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
crc32c_intel           24576  1
video                  61440  0
ghash_clmulni_intel    16384  0
vboxguest             421888  2
serio_raw              20480  0
dm_mirror              28672  0
dm_region_hash         24576  1 dm_mirror
dm_log                 24576  2 dm_region_hash,dm_mirror
dm_mod                204800  9 dm_log,dm_mirror


[root@localhost cdrom0]# ps afx
    PID TTY      STAT   TIME COMMAND
      2 ?        S      0:00 [kthreadd]
      3 ?        I<     0:00  \_ [rcu_gp]
      4 ?        I<     0:00  \_ [rcu_par_gp]
      5 ?        I<     0:00  \_ [slub_flushwq]
      6 ?        I<     0:00  \_ [netns]
      8 ?        I<     0:00  \_ [kworker/0:0H-events_highpri]
      9 ?        I      0:00  \_ [kworker/u2:0-writeback]
     10 ?        I<     0:00  \_ [kworker/0:1H-events_highpri]
     11 ?        I<     0:00  \_ [mm_percpu_wq]
     13 ?        I      0:00  \_ [rcu_tasks_kthre]
     14 ?        I      0:00  \_ [rcu_tasks_rude_]
     15 ?        I      0:00  \_ [rcu_tasks_trace]
     16 ?        S      0:00  \_ [ksoftirqd/0]
     17 ?        I      0:00  \_ [rcu_preempt]
     18 ?        S      0:00  \_ [migration/0]
     20 ?        S      0:00  \_ [cpuhp/0]
     22 ?        S      0:00  \_ [kdevtmpfs]
     23 ?        I<     0:00  \_ [inet_frag_wq]
     24 ?        S      0:00  \_ [kauditd]
     25 ?        S      0:00  \_ [khungtaskd]
     26 ?        S      0:00  \_ [oom_reaper]
     28 ?        I<     0:00  \_ [writeback]
     29 ?        S      0:00  \_ [kcompactd0]
     30 ?        SN     0:00  \_ [ksmd]
     31 ?        SN     0:00  \_ [khugepaged]
     32 ?        I<     0:00  \_ [cryptd]
     33 ?        I<     0:00  \_ [kintegrityd]
     34 ?        I<     0:00  \_ [kblockd]
     35 ?        I<     0:00  \_ [blkcg_punt_bio]
     36 ?        I<     0:00  \_ [tpm_dev_wq]
     37 ?        I<     0:00  \_ [md]
     38 ?        I<     0:00  \_ [edac-poller]
     39 ?        S      0:00  \_ [watchdogd]
     40 ?        S      0:00  \_ [kswapd0]
     45 ?        I<     0:00  \_ [kthrotld]
     49 ?        I<     0:00  \_ [acpi_thermal_pm]
     50 ?        I<     0:00  \_ [kmpath_rdacd]
     51 ?        I<     0:00  \_ [kaluad]
     53 ?        I<     0:00  \_ [mld]
     54 ?        I<     0:00  \_ [ipv6_addrconf]
     55 ?        I<     0:00  \_ [kstrp]
     67 ?        I<     0:00  \_ [zswap-shrink]
    186 ?        I<     0:00  \_ [kworker/u3:0]
    386 ?        I<     0:00  \_ [iprt-VBoxWQueue]
    388 ?        I<     0:00  \_ [ata_sff]
    389 ?        S      0:00  \_ [scsi_eh_0]
    390 ?        I<     0:00  \_ [scsi_tmf_0]
    391 ?        S      0:00  \_ [scsi_eh_1]
    392 ?        S      0:00  \_ [scsi_eh_2]
    393 ?        I<     0:00  \_ [scsi_tmf_1]
    394 ?        I<     0:00  \_ [scsi_tmf_2]
    465 ?        I<     0:00  \_ [kdmflush/253:0]
    472 ?        I<     0:00  \_ [kdmflush/253:1]
    490 ?        I<     0:00  \_ [xfsalloc]
    491 ?        I<     0:00  \_ [xfs_mru_cache]
    492 ?        I<     0:00  \_ [xfs-buf/dm-0]
    493 ?        I<     0:00  \_ [xfs-conv/dm-0]
    494 ?        I<     0:00  \_ [xfs-reclaim/dm-]
    495 ?        I<     0:00  \_ [xfs-blockgc/dm-]
    496 ?        I<     0:00  \_ [xfs-inodegc/dm-]
    497 ?        I<     0:00  \_ [xfs-log/dm-0]
    498 ?        I<     0:00  \_ [xfs-cil/dm-0]
    499 ?        S      0:00  \_ [xfsaild/dm-0]
    614 ?        I<     0:00  \_ [xfs-buf/sda1]
    615 ?        I<     0:00  \_ [xfs-conv/sda1]
    616 ?        I<     0:00  \_ [xfs-reclaim/sda]
    617 ?        I<     0:00  \_ [xfs-blockgc/sda]
    618 ?        I<     0:00  \_ [xfs-inodegc/sda]
    619 ?        I<     0:00  \_ [xfs-log/sda1]
    620 ?        I<     0:00  \_ [xfs-cil/sda1]
    621 ?        S      0:00  \_ [xfsaild/sda1]
    677 ?        S      0:00  \_ [irq/18-vmwgfx]
    678 ?        S      0:00  \_ [card0-crtc0]
    680 ?        S      0:00  \_ [card0-crtc1]
    681 ?        S      0:00  \_ [card0-crtc2]
    682 ?        S      0:00  \_ [card0-crtc3]
    683 ?        S      0:00  \_ [card0-crtc4]
    685 ?        S      0:00  \_ [card0-crtc5]
    686 ?        S      0:00  \_ [card0-crtc6]
    688 ?        S      0:00  \_ [card0-crtc7]
   5177 ?        I      0:01  \_ [kworker/0:3-events_freezable_power_]
  17145 ?        I      0:00  \_ [kworker/u2:1-events_unbound]
  17503 ?        I      0:00  \_ [kworker/0:1-ata_sff]
  17618 ?        I      0:00  \_ [kworker/0:0-ata_sff]
  17621 ?        I      0:00  \_ [kworker/u2:2-events_unbound]
      1 ?        Ss     0:02 /usr/lib/systemd/systemd --switched-root --system --deserialize 31
    562 ?        Ss     0:00 /usr/lib/systemd/systemd-journald
    575 ?        Ss     0:00 /usr/lib/systemd/systemd-udevd
    628 ?        S<sl   0:00 /sbin/auditd
    658 ?        Ssl    0:00 /usr/bin/python3 -s /usr/sbin/firewalld --nofork --nopid
    659 ?        Ssl    0:00 /usr/sbin/rsyslogd -n
    663 ?        Ss     0:00 /usr/lib/systemd/systemd-logind
    670 ?        S      0:00 /usr/sbin/chronyd -F 2
    673 ?        Ss     0:00 /usr/bin/dbus-broker-launch --scope system --audit
    675 ?        S      0:00  \_ dbus-broker --log 4 --controller 9 --machine-id 259824bdf2d1434e8f5f5ce5aed918ab --max-bytes 536870912 --max-fds 4096
    716 ?        Ssl    0:00 /usr/sbin/NetworkManager --no-daemon
    740 ?        Ss     0:00 sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups
   1522 ?        Ss     0:00  \_ sshd: erickos [priv]
   1537 ?        S      0:00      \_ sshd: erickos@pts/0
   1538 pts/0    Ss     0:00          \_ -bash
   1573 pts/0    S      0:00              \_ sudo -i
   1575 pts/0    S      0:00                  \_ -bash
  17626 pts/0    R+     0:00                      \_ ps afx
    760 ?        Ss     0:00 /usr/sbin/crond -n
    762 ?        Ss     0:00 login -- root
   1484 tty1     Ss+    0:00  \_ -bash
    862 ?        Ssl    0:00 /usr/lib/polkit-1/polkitd --no-debug
   1237 ?        Sl     0:00 /usr/bin/VBoxDRMClient
   1474 ?        Ss     0:00 /usr/lib/systemd/systemd --user
   1476 ?        S      0:00  \_ (sd-pam)
   1527 ?        Ss     0:00 /usr/lib/systemd/systemd --user
   1529 ?        S      0:00  \_ (sd-pam)
  17462 ?        Sl     0:00 /usr/sbin/VBoxService --pidfile /var/run/vboxadd-service.sh


[root@localhost cdrom0]# hostname -I
10.0.2.15 192.168.56.102


[root@localhost cdrom0]# ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:8f:58:d9 brd ff:ff:ff:ff:ff:ff
    altname enp0s3
    inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic noprefixroute eth0
       valid_lft 85446sec preferred_lft 85446sec
    inet6 fe80::b3fc:60b4:a3ce:7209/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:15:b8:a9 brd ff:ff:ff:ff:ff:ff
    altname enp0s8
    inet 192.168.56.102/24 brd 192.168.56.255 scope global dynamic noprefixroute eth1
       valid_lft 546sec preferred_lft 546sec
    inet6 fe80::cf06:699f:5db1:ec76/64 scope link noprefixroute
       valid_lft forever preferred_lft forever


[root@localhost cdrom0]# ip route show
default via 10.0.2.2 dev eth0 proto dhcp src 10.0.2.15 metric 100
10.0.2.0/24 dev eth0 proto kernel scope link src 10.0.2.15 metric 100
192.168.56.0/24 dev eth1 proto kernel scope link src 192.168.56.102 metric 101


[root@localhost cdrom0]# cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 10.0.2.3


[root@localhost cdrom0]# netstat -ntulp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      740/sshd: /usr/sbin
tcp6       0      0 :::22                   :::*                    LISTEN      740/sshd: /usr/sbin
udp        0      0 127.0.0.1:323           0.0.0.0:*                           670/chronyd
udp6       0      0 ::1:323                 :::*                                670/chronyd


[root@localhost cdrom0]# ping -c 4 1.1.1.1
PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
64 bytes from 1.1.1.1: icmp_seq=1 ttl=63 time=128 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=63 time=152 ms
64 bytes from 1.1.1.1: icmp_seq=3 ttl=63 time=71.4 ms
64 bytes from 1.1.1.1: icmp_seq=4 ttl=63 time=94.0 ms

--- 1.1.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 71.356/111.367/152.273/31.004 ms


[root@localhost cdrom0]# dig example.com.

; <<>> DiG 9.16.23-RH <<>> example.com.
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 36883
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;example.com.			IN	A

;; ANSWER SECTION:
example.com.		6621	IN	A	93.184.216.34

;; Query time: 97 msec
;; SERVER: 10.0.2.3#53(10.0.2.3)
;; WHEN: Tue Feb 21 20:09:44 CST 2023
;; MSG SIZE  rcvd: 56

```

### Privilegios

```bash
[erickos@localhost ~]$ getent passwd ${USER}
erickos:x:1000:1000::/home/erickos:/bin/bash


[erickos@localhost ~]$ id
uid=1000(erickos) gid=1000(erickos) groups=1000(erickos),10(wheel),987(wireshark) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023


[erickos@localhost ~]$ groups
erickos wheel wireshark


[erickos@localhost ~]$ sudo -l
Matching Defaults entries for erickos on localhost:
    !visiblepw, always_set_home, match_group_by_gid, always_query_group_plugin, env_reset, env_keep="COLORS DISPLAY HOSTNAME HISTSIZE KDEDIR
    LS_COLORS", env_keep+="MAIL PS1 PS2 QTDIR USERNAME LANG LC_ADDRESS LC_CTYPE", env_keep+="LC_COLLATE LC_IDENTIFICATION LC_MEASUREMENT
    LC_MESSAGES", env_keep+="LC_MONETARY LC_NAME LC_NUMERIC LC_PAPER LC_TELEPHONE", env_keep+="LC_TIME LC_ALL LANGUAGE LINGUAS _XKB_CHARSET
    XAUTHORITY", secure_path=/sbin\:/bin\:/usr/sbin\:/usr/bin

User erickos may run the following commands on localhost:
    (ALL) NOPASSWD: ALL


[erickos@localhost ~]$ sudo -i
[root@localhost ~]#


```

### Ubicación de herramientas

```bash
[erickos@localhost ~]$ which wireshark tcpdump nmap netcat-openbsd ngrep dsniff wget curl whois dnsutils net-tools iproute2 iptables iptables-persistent tsocks inetutils-ping inetutils-traceroute inetutils-tools
/usr/bin/wireshark
/usr/sbin/tcpdump
/usr/bin/nmap
/usr/bin/which: no netcat-openbsd in (/home/erickos/.local/bin:/home/erickos/bin:/usr/share/Modules/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin)
/usr/sbin/ngrep
/usr/sbin/dsniff
/usr/bin/wget
/usr/bin/curl
/usr/bin/whois
/usr/bin/which: no dnsutils in (/home/erickos/.local/bin:/home/erickos/bin:/usr/share/Modules/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin)
/usr/bin/which: no net-tools in (/home/erickos/.local/bin:/home/erickos/bin:/usr/share/Modules/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin)
/usr/bin/which: no iproute2 in (/home/erickos/.local/bin:/home/erickos/bin:/usr/share/Modules/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin)
/usr/sbin/iptables
/usr/bin/which: no iptables-persistent in (/home/erickos/.local/bin:/home/erickos/bin:/usr/share/Modules/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin)
/usr/bin/which: no tsocks in (/home/erickos/.local/bin:/home/erickos/bin:/usr/share/Modules/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin)
/usr/bin/which: no inetutils-ping in (/home/erickos/.local/bin:/home/erickos/bin:/usr/share/Modules/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin)
/usr/bin/which: no inetutils-traceroute in (/home/erickos/.local/bin:/home/erickos/bin:/usr/share/Modules/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin)
/usr/bin/which: no inetutils-tools in (/home/erickos/.local/bin:/home/erickos/bin:/usr/share/Modules/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin)


[erickos@localhost ~]$ whereis wireshark tcpdump nmap netcat-openbsd ngrep dsniff wget curl whois dnsutils net-tools iproute2 iptables iptables-persistent tsocks inetutils-ping inetutils-traceroute inetutils-tools ethtool
wireshark: /usr/bin/wireshark /usr/lib64/wireshark /usr/share/wireshark /usr/share/man/man1/wireshark.1.gz
tcpdump: /usr/sbin/tcpdump /usr/share/man/man8/tcpdump.8.gz
nmap: /usr/bin/nmap /usr/share/nmap /usr/share/man/man1/nmap.1.gz
netcat-openbsd:
ngrep: /usr/sbin/ngrep /usr/share/man/man8/ngrep.8.gz
dsniff: /usr/sbin/dsniff /etc/dsniff /usr/share/man/man8/dsniff.8.gz
wget: /usr/bin/wget /usr/share/man/man1/wget.1.gz /usr/share/info/wget.info.gz
curl: /usr/bin/curl /usr/share/man/man1/curl.1.gz
whois: /usr/bin/whois /usr/share/man/man1/whois.1.gz
dnsutils:
net-tools:
iproute2: /etc/iproute2
iptables: /usr/sbin/iptables /usr/libexec/iptables /usr/share/man/man8/iptables.8.gz
iptables-persistent:
tsocks:
inetutils-ping:
inetutils-traceroute:
inetutils-tools:
ethtool: /usr/sbin/ethtool /usr/share/man/man8/ethtool.8.gz
```
