---
layout: post
title: TryHackMe | AnonForce
categories: TryHackMe
---

# TryHackMe | AnonForce

+++++++++++++++++++++++++++++++++++\
IP: 10.10.238.30\
Date: 12-12-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

![image](https://user-images.githubusercontent.com/115549820/207117690-45f166ef-2b13-4623-9ada-cf3be2c92394.png)

**Open Ports**

21 - FTP - vsftpd 3.0.3\
22 - SSH - OpenSSH 7.2p2

### FTP Enumeration

> Credential:
> ftp::ftp

![image](https://user-images.githubusercontent.com/115549820/207118092-b7892209-843f-4184-b858-2315230d836f.png)

![image](https://user-images.githubusercontent.com/115549820/207119591-345b604c-a6f5-4cb3-b1d5-915a27b5c0a4.png)

![image](https://user-images.githubusercontent.com/115549820/207120098-a577f7ed-b1f8-4a8e-9dd6-c203936d694a.png)

![image](https://user-images.githubusercontent.com/115549820/207121322-678fe68a-ef0e-4170-a1dd-a30dd4782c62.png)

![image](https://user-images.githubusercontent.com/115549820/207121445-81832bf9-425a-4e61-b501-86ee8d4f8ebd.png)

> Credential:\
> melodias::??

![image](https://user-images.githubusercontent.com/115549820/207121793-cb49bc12-4746-4dc5-8a17-3a9d95a50fe0.png)

![image](https://user-images.githubusercontent.com/115549820/207121886-e900766b-6794-4b0e-9472-7460f9ac4adb.png)

![image](https://user-images.githubusercontent.com/115549820/207126155-16c592bf-c1a0-4ffb-9f1c-1478362035a6.png)

![image](https://user-images.githubusercontent.com/115549820/207126740-788be689-7632-470b-825f-1c74f86d365d.png)

![image](https://user-images.githubusercontent.com/115549820/207126784-f0eac2ef-b851-4c5f-9300-37ea87f1767c.png)

![image](https://user-images.githubusercontent.com/115549820/207127031-56ddc2d0-33c9-4ee8-895e-3c4b443195d9.png)

![image](https://user-images.githubusercontent.com/115549820/207127081-5cd70da5-ea8c-4989-bff6-eb3106d9c128.png)

https://blog.atucom.net/2015/08/cracking-gpg-key-passwords-using-john.html

![image](https://user-images.githubusercontent.com/115549820/207127227-2fe7b2de-0e11-4972-88bb-c5bb740f16d2.png)

![image](https://user-images.githubusercontent.com/115549820/207127273-95c073d2-05e1-4d39-9391-0432954d3a1c.png)

![image](https://user-images.githubusercontent.com/115549820/207128188-1a722700-4a65-4ac7-a601-8837eb65cff6.png)


## Fase 2: Getting Access

![image](https://user-images.githubusercontent.com/115549820/207128255-67af9438-59bd-4cd8-b592-0496400d24b4.png)

![image](https://user-images.githubusercontent.com/115549820/207128893-f7040769-6eb7-4460-b64d-ccd2e9168d4c.png)

![image](https://user-images.githubusercontent.com/115549820/207132133-d358ff88-f8fb-4cbd-a9ff-7a1866a9e907.png)

![image](https://user-images.githubusercontent.com/115549820/207132232-d959d9a5-82e4-43c0-acf7-4356379b33b2.png)

![image](https://user-images.githubusercontent.com/115549820/207132278-7735d377-a656-40af-935f-cf3a3ec749f2.png)

![image](https://user-images.githubusercontent.com/115549820/207134840-37259ac6-da79-443e-89d0-c9178aa7e564.png)

![image](https://user-images.githubusercontent.com/115549820/207130813-2a750a0f-e78f-4700-92c1-8bd9fade968c.png)

![image](https://user-images.githubusercontent.com/115549820/207130868-a6132c4e-f4be-451f-8996-f16594048cb7.png)

![image](https://user-images.githubusercontent.com/115549820/207134888-a16aa26c-69a2-462c-96f2-f70fa63adcf1.png)

![image](https://user-images.githubusercontent.com/115549820/207134950-77b1c16e-7de2-4a65-a825-efd57302c253.png)

> Credential:\
> root::hikari

  
## Fase 3: Intern Enumeration

![image](https://user-images.githubusercontent.com/115549820/207135378-b03f1866-6bb7-47fa-aefd-c93dba0c504d.png)

![image](https://user-images.githubusercontent.com/115549820/207135502-7b52c11f-0dae-47e5-8888-eb8411a50449.png)
    
## TryHackMe Questions

user.txt
> 606083fd33beb1284fc51f411a706af8

root.txt
> f706456440c7af4187810c31c6cebdce
