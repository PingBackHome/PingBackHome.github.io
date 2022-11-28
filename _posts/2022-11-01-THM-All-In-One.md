---
layout: post
title: TryHackMe | All in one
categories: TryHackMe
---

# TryHackMe | All in one

+++++++++++++++++++++++++++++++++++\
IP: 10.10.104.160\
Date: 01-11-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199254565-571afee0-df87-43b5-b383-3ecb29b92798.png">

**Open Ports**

21 - FTP - vsftpd 3.0.3\
22 - SSH - OpenSSH 7.6p1\
80 - Webserver - Apache 2.4.29

### FTP Enumeration

<img width="350" alt="image" src="https://user-images.githubusercontent.com/115549820/199951387-fe7db85f-ebab-4449-ad98-3c3648d1dcb1.png">

### Webserver Enumeration

**Nikto Output**

<img width="750" alt="image" src="https://user-images.githubusercontent.com/115549820/199948803-db84a1f4-2107-42b7-aa9b-051e539f05bd.png">

**Dirbuster Output**

<img width="759" alt="image" src="https://user-images.githubusercontent.com/115549820/199948930-6cff5d1e-c9f7-4cb5-8a6d-90d25140ed1c.png">

**Homepage**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199949038-edc9dcc6-f364-407f-bcf4-c5f2bd1697f9.png">

**WordPress**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199949204-30eaea03-6bb8-440b-b26a-546783fe86f2.png">

***WP-login***

<img width="407" alt="image" src="https://user-images.githubusercontent.com/115549820/199952141-7462129f-c415-4a55-870f-519f216688f8.png">

***Possible username***

> elyana

**Wpscan**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199950233-4b5cffd8-7300-499b-8d30-05d80d427ad3.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199950341-14bf3095-15ec-4a40-8ee8-000d71a18cfb.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199950417-ba9575e2-e722-402c-a242-1843e00ca643.png">


## Fase 2: Getting Access

**Search for Exploit**

<img width="750" alt="image" src="https://user-images.githubusercontent.com/115549820/199952959-6c7df5bf-fb95-4420-9652-cae131c4a113.png">

<img width="750" alt="image" src="https://user-images.githubusercontent.com/115549820/199953053-369bda26-9b56-4735-aee6-08354702cbd1.png">

https://medium.com/@nyomanpradipta120/local-file-inclusion-vulnerability-cfd9e62d12cb

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200280648-eb15885c-5943-4c5b-b0a1-9f6f5d18b6e6.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200280883-100826c8-ade9-4d0e-91e8-ed9884edcd73.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200281023-b41b8efa-5280-4d6c-97cc-dd3de46c458a.png">

Creds for wordpress:
>elyana::H@ckme@123

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200283610-358da385-7a9e-4270-a36c-1eac8bca4ffd.png">

<img width="200" alt="image" src="https://user-images.githubusercontent.com/115549820/200283741-7af935f8-a673-41c7-9c05-87decc7b037c.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200283857-2b3951a8-b24e-4e0a-9979-ab254b4f16f2.png">

  
## Fase 3: Intern Enumeration

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200284173-c667ce1d-ed4c-435f-9c78-763aadae453b.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200285924-2be72e0f-182d-48e8-9875-33e348272198.png">

<img width="250" alt="image" src="https://user-images.githubusercontent.com/115549820/200286041-06160e0f-6c2b-4029-ae12-1492e076f4ab.png">

<img width="250" alt="image" src="https://user-images.githubusercontent.com/115549820/200286217-802b916e-3646-4d0d-a5b2-50786b11b758.png">

Creds:
> elyana::E@syR18ght

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200288765-1e5ab5a3-2110-415b-9b34-a053f2dc9e08.png">
  
## Fase 4: PrivEsc

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200289158-aac9d1c4-86b7-4e8a-bb19-51efe344f4bc.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200288960-07ee701e-647a-43f9-bc5b-b3f2b01b1be3.png">

<img width="825" alt="image" src="https://user-images.githubusercontent.com/115549820/200289452-9e8297b3-cb37-46ef-8e81-85e0b055113e.png">

<img width="825" alt="image" src="https://user-images.githubusercontent.com/115549820/200289680-bc265325-a3ae-4e62-ba18-efa761ef693b.png">

<img width="825" alt="image" src="https://user-images.githubusercontent.com/115549820/200289851-98e9fc34-2e72-4705-83e8-793450b2bc71.png">

  
## TryHackMe Questions

user.txt
> THM{49jg666alb5e76shrusn49jg666alb5e76shrusn}

root.txt
> THM{uem2wigbuem2wigb68sn2j1ospi868sn2j1ospi8}
