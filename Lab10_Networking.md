# Linux Networking

  1) Debian 13.x
  2) Ubuntu 24.04.4 LTS
  3) Rocky 9.x
  4) openEuler 24.03 LTS SP3
  5) Oracle 7.9

### Network Topology
![Topology](./images/image.png)

## Debian 13.x

#### System Information

```shell
student@debian:~$ lsb_release -a
Distributor ID: Debian
Description:    Debian GNU/Linux
Release:        13
Codename:       trixie

student@debian:~$ cat /etc/debian_version
13.5

student@debian:~$ uname -rs
Linux
```

#### Configure Device Hostname

```shell
$ sudo hostnamectl set-hostname node1

$ sudo nano /etc/hosts
127.0.1.1  node1

CTRL+O, ENTER, CTRL+X
CTRL+L

$ bash
```

#### Configure Network interface

```shell
$ ip address
```

```shell
$ sudo nano /etc/network/interfaces
  # allow-hotplug ens3
  auto ens3
  iface ens3 inet static
    address 10.10.10.101
    netmask 255.255.255.0
    gateway 10.10.10.1
    dns-nameservers 8.8.8.8

CTRL+O, ENTER, CTRL+X
CTRL+L
```

```shell
$ sudo systemctl restart networking
```

```shell
$ ip address
$ ip route
$ cat /etc/resolv.conf
```

## Ubuntu 24.04.4 LTS

#### System Information

```shell
student@ubuntu:~$ lsb_release -a
Ubuntu 24.04.4 LTS
Codename: noble

student@ubuntu:~$ uname -rs
Linux 6.8.0-101-generic x86_64 GNU/Linux
```

#### Configure Device Hostname

```shell
$ sudo hostnamectl set-hostname node2

$ sudo nano /etc/hosts
127.0.1.1  node2

CTRL+O, ENTER, CTRL+X
CTRL+L

$ bash
```

#### Configure Network interface

```shell
$ ip address
```

```shell
student@ubuntu:~$ sudo nano /etc/netplan/50-cloud-init.yaml
network:
  version: 2
  ethernets:
    ens3:
      addresses:
      - "10.10.10.123/24"
      nameservers:
        addresses:
        - 8.8.8.8
        search:
        - LAB.LOCAL
      routes:
      - to: "default"
        via: "10.10.10.1"

CTRL+O, ENTER, CTRL+X
CTRL+L
```

немесе

```shell
student@ubuntu:~$ sudo nano /etc/netplan/50-cloud-init.yaml
network:
  version: 2
  ethernets:
    ens3:
      dhcp4: false
      addresses: [10.10.10.123/24]
      gateway4: 10.10.10.1
      nameservers:
        search: [lab.local]
        addresses: [8.8.8.8]

CTRL+O, ENTER, CTRL+X
CTRL+L
```
> **ЕСКЕРТУ:** *YAML файлында бос орындар (indentation) өте маңызды. Әр қатарда 2 бос орын қолдануды ұмытпаңыз! (Tab пернесін қолданбаған дұрыс)*  

```shell
$ sudo netplan apply
немесе
$ sudo netplan try
```

```shell
$ ip address
$ ip route
$ resolvectl status
```

```shell
$ networkctl status
```
