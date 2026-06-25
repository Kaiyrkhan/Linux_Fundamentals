# How to install Debian

Table - Minimum System Requirements
| Component | Minimum Requirement |
|-----------|---------------------|
| Processor | 1 GHz single-core   |
| Memory    | 2 GB RAM            |
| Storage   | 20 GB               |

![images](./images/debian_installer_menu.png)
![images](./images/debian_select_language.png)
![images](./images/debian_select_location_country_other.png)
![images](./images/debian_select_location_region.png)
![images](./images/debian_select_location_country_kz.png)
![images](./images/debian_configure_locales.png)
![images](./images/debian_configure_keyboard.png)
![images](./images/debian_configure_hostname.png)
![images](./images/debian_configure_domain-name.png)
![images](./images/debian_root_password.png)
![images](./images/debian_root_password_verify.png)
![images](./images/debian_newuser_fullname.png)
![images](./images/debian_newuser_username.png)
![images](./images/debian_newuser_password.png)
![images](./images/debian_newuser_password_verify.png)
![images](./images/debian_configure_timezone.png)
![images](./images/debian_partition_method.png)
![images](./images/debian_select_disk.png)
![images](./images/debian_partition_scheme.png)
![images](./images/debian_partition_finish.png)
![images](./images/debian_partition_change_write.png)
![images](./images/debian_scan_media.png)
![images](./images/debian_archive_mirror_country.png)
![images](./images/debian_archive_mirror.png)
![images](./images/debian_http_proxy.png)
![images](./images/debian_survey.png)
![images](./images/debian_software_selection.png)
![images](./images/debian_install_grub.png)
![images](./images/debian_install_grub_device.png)
![images](./images/debian_installation_complete.png)

**1-қадам: Add a User to the Sudo Group**

debian login: **root**  
password: **P@s$w0rd**  

```shell
root@debian:~# usermod -aG sudo student
root@debian:~# groups student
```

```shell
root@debian:~# ping -c2 google.com
root@debian:~# apt install sudo
root@debian:~# reboot
```

**2-қадам: Update and Upgrade**

debian login: **student**  
password: **123**  

```shell
student@debian:~$ sudo apt update
student@debian:~$ sudo apt upgrade -y
```

**3-қадам: System Information**
```shell
student@debian:~$ uname -sr
student@debian:~$ lsb_release -a
student@debian:~$ cat /etc/debian_version
```

**4-қадам: Verify SSH Connectivity**
```shell
student@debian:~$ sudo systemctl status ssh

student@debian:~$ ip address
```

**5-қадам: Banner Messages**

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

**6-қадам: Clear Bash History**

```shell
student@debian:~$ history

student@debian:~$ ls -la
student@debian:~$ cat /dev/null > ~/.bash_history
student@debian:~$ history -c
```

```shell
student@debian:~$ logout

debian login: root
password: P@s$w0rd

root@debian:~#
```

```shell
root@debian:~# history

root@debian:~# ls -la
root@debian:~# cat /dev/null > ~/.bash_history
root@debian:~# history -c

root@debian:~# reboot
```

**7-қадам: Power Off**
```shell
student@debian:~$ sudo poweroff
```

![images](./images/vmware_hardware_devices.png)  

**8-қадам: Description**  

VMware Workstation -> Description  

Username: student  
Password: 123  

Username: root  
Password: P@s$w0rd  

**9-қадам: I Copied It**

`*.vmx` файлды ашып, төмендегі команданы енгіземіз!  
```shell
uuid.action = "create"
```
> C:\Users\student\Documents\Virtual Machines\debian-13.5\  

**10-қадам: Export to OVF**

![images](./images/vmware_export_to_ovf.png)  

Нәтижесінде төмендегідей 3 файл құрылады:  
  1) `*.mf`   - Manifest File
  2) `*.vmdk` - Virtual Machine Disk
  3) `*.ovf`  - Open Virtualization Format

**11-қадам: VMware OVF Tool арқылы OVA файл құру**

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
![images](./images/debian_dir_ovf_files.png)

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
![images](./images/debian_dir_ova_ovf_files.png)

**12-қадам: Take Snapshot**  
  
Snapshot Manager -> Take Snapshot -> initial image  
