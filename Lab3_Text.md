# Text Editors and Text Processing

### nano (Text Editor)

```shell
«Alt + \» — файлдың басына өту
«Alt + /» — файлдың соңына өту

«Alt + 6» — мәтінді белгілеу (Set Mark)
«Ctrl + Shift + 6» — егер PuTTY-де отырсаңыз, мәтінді белгілеу (Set Mark)

«Ctrl + K» — мәтінді buffer-ге қиып алу
```

| nano    | vi/vim (Normal mode) |
|---------|----------------------|
| Alt + \ | gg                   |
| Alt + / | G                    |
|         | Shift+{              |
|         | Shift+}              |

```shell
root@debian:~# cat >> /etc/hosts <<EOF
10.10.10.67 dhcp
EOF
```

```shell
$ ip a
$ ip -br a
```

```shell
$ sudo grep -RIn "text" /etc /home/student 2>/dev/null
```

### vi/vim

`i` - Edit mode  
`ESC` - Normal mode  
