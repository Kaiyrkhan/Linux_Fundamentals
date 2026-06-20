# How to install Debian

Table - Minimum System Requirements
| Component | Minimum Requirement |
|-----------|---------------------|
| Processor | 1 GHz single-core   |
| Memory    | 2 GB RAM            |
| Storage   | 25 GB               |

```shell
root@debian:~# groups student
root@debian:~# usermod -aG sudo student
root@debian:~# groups student
```

```shell
root@debian:~# ping -c2 google.com
root@debian:~# apt install sudo
root@debian:~# reboot
```

```shell
student@debian:~$ sudo apt update
student@debian:~$ sudo apt upgrade -y
```

```shell
student@debian:~$ uname -sr
student@debian:~$ lsb_release -a
student@debian:~$ cat /etc/debian_version
```

```shell
student@debian:~$ ip address

student@debian:~$ sudo systemctl status sshd
```

Verify SSH Connectivity

```shell
student@debian:~$ sudo reboot
student@debian:~$ sudo poweroff
```

Snapshot Manager -> Take Snapshot -> initial image  

```shell
student@debian:~$ sudo nano /etc/issue
\S \l
Kernel \r

************************************
Username: student
Password: 123
************************************

CTRL+O, ENTER, CTRL+X
CTRL+L
```

