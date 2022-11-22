---
layout: post
title: TryHackMe | Wgel CTF
---

# TryHackMe | Wgel CTF

+++++++++++++++++++++++++++++++++++\
IP: 10.10.7.192\
Date: 31-10-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199023337-286a467d-77c5-4f64-b492-a85c896fdb3d.png">

**Open Ports**

22 - SSH - OpenSSH 7.2p2\
80 - Webserver - Apache 2.4.18

### Webserver Enumeration

**Nikto output**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199025078-adfec294-2708-4589-b4d8-aba4e715ba84.png">

**Dirbuster output**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199026104-27d526e3-9942-4e25-a9d4-40ae32bcb237.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199026274-b4bac316-5db8-4e1a-8f23-e58924fc25c2.png">

**/index.html**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199024787-5da0e9c3-c1e6-43c7-bcb9-e4264ce5167b.png">

***/index.html - source code***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199024971-995f55e2-1013-4000-b262-bf09d511a686.png">

***/sitemap/.ssh***

<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/199026545-548a26ab-1f8f-4654-a00d-aa2af1302de3.png">

<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/199026637-4a6c7fb5-81ee-4c09-8531-2a6a54a633e9.png">

<img width="200" alt="image" src="https://user-images.githubusercontent.com/115549820/199026907-968e54d2-0743-4197-a122-ce11a51dcc4c.png">


## Fase 2: Getting Access

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199027350-feee2a75-ff76-4bd8-a98b-dc7569fceabf.png">

  
## Fase 3: Intern Enumeration

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199027713-8d803152-9104-4707-b0ac-f2ce074e5815.png">

  
## Fase 4: PrivEsc

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199028953-352617dd-ae07-48aa-9327-084693fa40b7.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199028867-2c1d10a1-59a1-40ac-9a81-262d21b1eb5e.png">

  
## TryHackMe Questions

'User flag?'
> 057c67131c3d5e42dd5cd3075b198ff6

'Root flag?'
> b1b968b37519ad1daa6408188649263d
