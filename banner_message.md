# Banner Messages

**Configure Console Login Banner**

```shell
student@debian:~$ sudo nano /etc/issue
\S \l
Kernel \r

**********************************
Username: student
Password: 123
**********************************
ENTER
ENTER

CTRL+O, ENTER, CTRL+X
CTRL+L
```
`\S` - OS name  
`\l` - TTY name  
`\r` - Kernel release  

```shell
student@debian:~$ logout
```

**Configure Remote Login Banner**

```shell
student@debian:~$ sudo nano /etc/issue.net

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
student@debian:~$ sudo nano /etc/ssh/sshd_config
Banner /etc/issue.net

student@debian:~$ sudo systemctl restart ssh
```

**MOTD (Message of the Day)**

```shell
student@debian:~$ sudo nano /etc/motd
```
