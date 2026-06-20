# How to install Ubuntu Server

Table - Minimum System Requirements
| Component | Minimum Requirement |
|-----------|---------------------|
| Processor | 1 GHz single-core   |
| Memory    | 2 GB RAM            |
| Storage   | 25 GB               |

**1-қадам: Set the Root Password**

```shell
student@ubuntu:~$ sudo passwd root
New password: P@s$w0rd
```

```shell
student@ubuntu:~$ groups student
```

**2-қадам: Update and Upgrade**
```shell
student@ubuntu:~$ ping google.com -c2

student@ubuntu:~$ sudo apt update
student@ubuntu:~$ sudo apt upgrade -y
```

**3-қадам: System Information**
```shell
student@ubuntu:~$ uname -sr
student@ubuntu:~$ lsb_release -a
```

**4-қадам: Verify SSH Connectivity**
```shell
student@ubuntu:~$ ip address
```

**5-қадам: Banner Messages**

**Configure Console Login Banner**

```shell
student@ubuntu:~$ sudo nano /etc/issue
\S \l
Kernel \r

************************
Username: student
Password: 123
************************
ENTER
ENTER

CTRL+O, ENTER, CTRL+X
CTRL+L
```
`\S` - OS name  
`\l` - TTY name  
`\r` - Kernel release  

**Configure Remote Login Banner**

```shell
student@ubuntu:~$ sudo nano /etc/issue.net

************************************
Authorized access only!
Unauthorized access is prohibited.
************************************
ENTER
ENTER

CTRL+O, ENTER, CTRL+X
CTRL+L
```

```shell
student@ubuntu:~$ sudo nano /etc/ssh/sshd_config
Banner /etc/issue.net

student@ubuntu:~$ sudo systemctl restart ssh
```

**6-қадам: Power Off**
```shell
student@ubuntu:~$ poweroff
```

**7-қадам: Description**  

VMware Workstation -> Description  

Username: student  
Password: 123  

Username: root  
Password: P@s$w0rd  

**8-қадам: Take Snapshot**  
  
Snapshot Manager -> Take Snapshot -> initial image  
