---
title: Faculty
published: true
---
**Escaneo**

sudo nmap -p- --open -sS --min-rate 5000 -vvv -n -Pn 10.10.11.169 -oG allPorts 

```bash
PORT   STATE SERVICE REASON
22/tcp open  ssh     syn-ack ttl 63
80/tcp open  http    syn-ack ttl 63
```

sudo nmap -sCV -p10.10.11.169-oN targeted

```bash
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   3072 e9:41:8c:e5:54:4d:6f:14:98:76:16:e7:29:2d:02:16 (RSA)
|   256 43:75:10:3e:cb:78:e9:52:0e:eb:cf:7f:fd:f6:6d:3d (ECDSA)
|_  256 c1:1c:af:76:2b:56:e8:b3:b8:8a:e9:69:73:7b:e6:f5 (ED25519)
80/tcp open  http    nginx 1.18.0 (Ubuntu)
|_http-title: Did not follow redirect to [http://faculty.htb](http://faculty.htb/)
|_http-server-header: nginx/1.18.0 (Ubuntu)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

Observamos el VHost para agregarlo en el /etc/hosts

**Enumeracion**

En la pagina web tenemos un campo para introducir informacion de login, asi que probaremos si es inyectable a SQLi con el siguiente payload `admin' or 1=1-- -`

![](/home/kali/WebServer/neuroproxy.github.io/assets/Faculty/primera-faculty.png)
