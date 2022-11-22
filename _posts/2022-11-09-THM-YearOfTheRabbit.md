---
layout: post
title: TryHackMe | Year of the Rabbit
---

# TryHackMe | Year of the Rabbit

+++++++++++++++++++++++++++++++++++\
IP: 10.10.75.188\
Date: 09-11-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/200789421-1733f310-8b03-49f5-b5cf-7b8d707b3b62.png">

**Open Ports**

21 - FTP - vsftpd 3.0.2\
22 - SSH - OpenSSH 6.7p1\
80 - Webserver - Apache 2.4.10

### Webserver Enumeration

**Nikto Output**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200793763-5832d239-1dad-4b4a-a0b3-2ceec0307c5f.png">

**Dirbuster Output**

Wordlist: directory-list-lowercase-2.3-small.txt\
Extentions:php, html, txt\
<img width="571" alt="image" src="https://user-images.githubusercontent.com/115549820/200795256-3e79977e-61cc-4716-a3fd-59cf672ddb6d.png">

Wordlist: common\
Extentions: php, txt, html\
<img width="571" alt="image" src="https://user-images.githubusercontent.com/115549820/200799659-ea29663f-0474-453b-9283-eaa0af4cd490.png">


***Homepage***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200794637-6b5607e2-cf49-480d-9ca4-c7ff30538299.png">

***/assets/style.css***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200794837-48eb6fc9-0b5d-49be-bfd6-ba73874399d7.png">

***/sup3r_s3cr3t_fl4g.php***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200794992-035f57e9-7586-45dc-a550-f9dd252f6114.png">

**Burpsuit Exploration**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200808498-707d3866-53c8-4db0-a416-9a7fa7b17c1e.png">

***/WExYY2Cv-qU***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200810729-224de22b-b15d-447e-aec2-a77c774b9716.png">

***Hot_Babe.png***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200811327-64234504-ead4-4cdb-b518-10a9941a851f.png">


### FTP Enumeration

<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/200794438-db7b85c0-c247-4c97-8a60-8d2df310c4a4.png">

**Cracking FTP creds**

<img width="350" alt="image" src="https://user-images.githubusercontent.com/115549820/200811608-457ab759-5d5c-4a84-8eb2-b6651c80547d.png">

<img width="350" alt="image" src="https://user-images.githubusercontent.com/115549820/200811778-120a9bdf-6e1d-45fa-9396-3b100ac61466.png">

Credentials FTP:\
> ftpuser::5iez1wGXKfPKQ

## Fase 2: Getting Access

**Acces to FTP server**

<img width="320" alt="image" src="https://user-images.githubusercontent.com/115549820/200812115-74f61c9b-5988-40b7-bca9-878b783acb66.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200812328-39fe8a22-45fa-4b67-9196-e363488d60e5.png">

***Eli's_Creds.txt***

<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/200812507-9b3cd0ec-d2d8-495e-afbc-58ab553cb059.png">

***Decode brainfuck code***

https://www.dcode.fr/brainfuck-language \
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/200812699-44b6eba7-4aa3-458c-b733-20020df24d4a.png">

Credentials SSH
> eli::DSpDiM1wAEwid

**Acces to SSH server**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200812957-5370fb07-bfc6-464d-9184-fb8f4351271c.png">

## Fase 3: Intern Enumeration

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200813384-0971fda9-9147-4bb3-9ad3-92d4e08ec895.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200813686-3c54059b-7373-4805-a0be-3617f8965920.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200814036-266ce006-0272-4631-9d98-d2253e004b1e.png">

**Uploading linpeas**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200820355-bd894173-788a-438a-a100-041bdfc1d4fc.png">

***Linpeas Output***

<img width="350" alt="image" src="https://user-images.githubusercontent.com/115549820/200821573-8d3d4ae8-75fb-4429-9e86-b9d4261fe3c0.png">

<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/200821866-bfc25f4e-6e1e-471d-a551-c976e125a4bc.png">

<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/200822154-08cd7487-caeb-4f5a-9537-b2bcdc310e25.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200822378-f44a83e5-c47a-4c10-94de-eddd072f3ad3.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200823224-6743edd0-eedf-41b3-a8a1-09b52a276ae9.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200824766-073f2f1f-d833-4ab2-9f77-dc5eed5ae638.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200824973-541bea65-7092-480e-b0f3-759e23ee6bfa.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200825052-e231247c-c920-46a9-b288-8299575f5e8e.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200825177-89ca634b-dd65-417b-a867-43ef78bca08d.png">

Credentials SSH Gwendoline
> gwendoline::MniVCQVhQHUNI
  
## Fase 4: PrivEsc

**Login w/ Gwendoline**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200825438-2999d088-cda5-4508-b57c-53b7cdab3195.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200825558-fc077189-1179-4ceb-a7cd-563d51efa84f.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200826125-0da6522d-bcb7-45ae-a7c7-6ef782e056e5.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200826210-f51157bb-42a9-47d6-8ae0-787ecdd4cae8.png">

***Priv Esc w/ VI***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200826408-f0d7d1ae-529b-4c1f-9c9d-4154913c7dbe.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200827443-53849783-fc06-4e5a-87e3-ff45eb74cec8.png">

***Priv Esc w/ sudo***

<img width="704" alt="image" src="https://user-images.githubusercontent.com/115549820/200829126-83839ee4-0811-4843-add3-12aa5516ddcc.png">

<img width="287" alt="image" src="https://user-images.githubusercontent.com/115549820/200829157-8d3dea7a-e860-4cb7-b19b-21e9b7cca37f.png">

<img width="368" alt="image" src="https://user-images.githubusercontent.com/115549820/200829232-b453bc15-57a7-4da1-827a-faee75d19c86.png">



## TryHackMe Questions

What is the user flag?
> THM{1107174691af9ff3681d2b5bdb5740b1589bae53}

What is the root flag?
> THM{8d6f163a87a1c80de27a4fd61aef0f3a0ecf9161}
