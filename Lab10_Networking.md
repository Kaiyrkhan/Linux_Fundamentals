# Linux Networking

  1) Debian 13.x
  2) Ubuntu 24.04.4 LTS
  3) Rocky 9.x
  4) openEuler 24.03 LTS SP3
  5) Oracle 7.9

### Network Topology
![Topology](./images/image.png)

## Ubuntu 24.04.4 LTS

```shell
student@ubuntu:~$ lsb_release -a
Ubuntu 24.04.4 LTS

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
student@ubuntu:~$ ip address
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
student@ubuntu:~$ sudo netplan apply
немесе
student@ubuntu:~$ sudo netplan try
```

```shell
student@ubuntu:~$ ip address
```

```shell
student@ubuntu:~$ networkctl status
```
