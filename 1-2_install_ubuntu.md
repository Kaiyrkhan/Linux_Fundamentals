# How to install Ubuntu Server

Table - Minimum System Requirements
| Component | Minimum Requirement |
|-----------|---------------------|
| Processor | 1 GHz single-core   |
| Memory    | 2 GB RAM            |
| Storage   | 25 GB               |

**1-қадам: Set the Root Password**

ubuntu login: **student**  
password: **123**  

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

```shell
student@ubuntu:~$ reboot
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

**6-қадам: optional: true**

```shell
student@ubuntu:~$ sudo nano /etc/netplan/50-cloud-init.yaml
network:
  version: 2
  ethernets:
    ens32:
      dhcp4: true
      optional: true

CTRL+O, ENTER, CTRL+X
CTRL+L

student@ubuntu:~$ sudo netplan apply
```

**7-қадам: Clear Bash History**

```shell
student@ubuntu:~$ history

student@ubuntu:~$ ls -la
student@ubuntu:~$ cat /dev/null > ~/.bash_history
student@ubuntu:~$ history -c
```

```shell
student@ubuntu:~$ logout

ubuntu login: root
password: P@s$w0rd

root@ubuntu:~#
```

```shell
root@ubuntu:~# history

root@ubuntu:~# ls -la
root@ubuntu:~# cat /dev/null > ~/.bash_history
root@ubuntu:~# history -c

root@ubuntu:~# reboot
```

**8-қадам: Power Off**
```shell
student@ubuntu:~$ poweroff
```

**9-қадам: I Copied It**

`*.vmx` файлды ашып, төмендегі команданы енгіземіз!  
```shell
uuid.action = "create"
```
> C:\Users\student\Documents\Virtual Machines\ubuntu-24.04.4-LTS\  

**10-қадам: Description**  

VMware Workstation -> Description  

Username: student  
Password: 123  

Username: root  
Password: P@s$w0rd  

**11-қадам: Export to OVF**

![images](./images/export_to_ovf.png)  

Нәтижесінде төмендегідей 3 файл құрылады:  
  1) `*.mf`   - Manifest File
  2) `*.vmdk` - Virtual Machine Disk
  3) `*.ovf`  - Open Virtualization Format

**12-қадам: VMware OVF Tool арқылы OVA файл құру**

Download OVF Tool https://developer.broadcom.com/tools/open-virtualization-format-ovf-tool/latest  

Terminal (PowerShell) -> Run as administrator  
```shell
cd "C:\Program Files\VMware\VMware OVF Tool"
.\ovftool.exe --version
```

```shell
cd "$env:USERPROFILE\Documents\Virtual Machines\OVF_files"
```

```shell
dir
```
![images](./images/dir_ovf_files.png)

OVF to OVA file
```shell
& "C:\Program Files\VMware\VMware OVF Tool\ovftool.exe" `
"debian-13.5.ovf" `
"debian-13.5.ova"
```
The manifest validates  
Transfer Completed  
Completed successfully  

```shell
dir
```
![images](./images/dir_ova_ovf_files.png)

**13-қадам: Take Snapshot**  
  
Snapshot Manager -> Take Snapshot -> initial image  
