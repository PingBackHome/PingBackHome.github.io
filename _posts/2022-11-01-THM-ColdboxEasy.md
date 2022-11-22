---
layout: post
title: TryHackMe | ColdBox Easy
---

# TryHackMe | Coldbox: Easy

+++++++++++++++++++++++++++++++++++\
IP: 10.10.238.160\
Date: 01-11-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199202072-fbc0866b-640e-44b1-ad89-365770e7434b.png">

**Open Ports**

80 - webserver - Apache 2.4.18\
4512 - SSH - OpenSSH 7.2p2


### Webserver Enumeration

**Nikto Output**

<img width="750" alt="image" src="https://user-images.githubusercontent.com/115549820/199203651-a8c455d8-9e99-45f1-b55e-5f3475622ec3.png">

**Dirbuster Output**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199202990-c737e025-a651-4ecb-b2de-eb65f7a6aeda.png">

***Homepage***

<img width="750" alt="image" src="https://user-images.githubusercontent.com/115549820/199203119-1f6e710b-7938-4048-aa4c-9a6043448e70.png">

***/hidden***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199203218-38415adf-8d65-4ceb-be23-035e67079af7.png">

***/xmlrpc.php***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199203472-d00ac009-8ac7-4f4a-b561-afdd7c89a648.png">

***/wp-login.php***

<img width="250" alt="image" src="https://user-images.githubusercontent.com/115549820/199203847-eec8494d-ac9f-45b3-9a58-2e098207b0fe.png">

**WPscan Output**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199204768-727f4e55-6f00-497c-a97e-58a3b18404d2.png">

Possible usernames:
- c0ldd
- phillip
- hugo

***WPscan Password***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199210206-9f56b43f-36ef-47ed-b834-7403f22f0cca.png">

Credentials WordPress
> c0ldd::9876543210

## Fase 2: Getting Access

**Acces to WP**

<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/199210717-4db1eaf1-bb5e-4834-8e1b-2f0095ee43d5.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199210840-e7847788-62e6-499b-afcd-f9969c2d917c.png">

***Upload reverse php shell***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199212068-54a76e2a-dd74-495b-921e-b14d29e28b4b.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199213765-a1eb3769-8cc9-4106-b703-6fa5bc8025c4.png">

<img width="250" alt="image" src="https://user-images.githubusercontent.com/115549820/199212302-b7556bca-21b4-43c8-b345-b47df9583094.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199213903-31550a51-25c6-41c6-b65f-aea6c151cb9e.png">
  
## Fase 3: Intern Enumeration

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199214134-dd407709-4f4c-4637-be68-caf2565145ea.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199215257-32d08c2a-f4e4-40d4-a171-a9a27cfddc32.png">

Box Credentials
> c0ldd::cybersecurity

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199216731-ce111b3e-fac5-464d-83b2-c59de7ce821d.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199216949-b5cf959e-8865-4b3e-9e6c-d11b3cdeb419.png">

<img width="450" alt="image" src="https://user-images.githubusercontent.com/115549820/199217052-ca00fa88-aad0-46fe-b989-13e2b5393316.png">
  
## Fase 4: PrivEsc

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199217575-2a6525bc-1652-4c42-8fc1-191cc06c2fc6.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199217918-05d56840-9e40-4791-b31b-27a1b64105b9.png">

<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/199218382-f574bec4-cbfc-493b-9559-01bfa0689999.png">

<img width="425" alt="image" src="https://user-images.githubusercontent.com/115549820/199218477-f2f5867c-0723-4fa8-88a4-dbaa2c9ef816.png">

<img width="425" alt="image" src="https://user-images.githubusercontent.com/115549820/199218564-c05d32dd-cefa-4cfa-89d9-62c269727c53.png">

## TryHackMe Questions

'user.txt'\
> RmVsaWNpZGFkZXMsIHByaW1lciBuaXZlbCBjb25zZWd1aWRvIQ==\
> SPANISH: Felicidades, primer nivel conseguido!\
> ENGLISH: Congratulations, first level achieved!

'root.txt'\
> wqFGZWxpY2lkYWRlcywgbcOhcXVpbmEgY29tcGxldGFkYSE=\
> SPANISH: ¡Felicidades, máquina completada!\
> ENGLISH: Congratulations, machine completed!
