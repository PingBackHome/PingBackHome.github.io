---
layout: post
title: TryHackMe | Chocolate Factory
categories: TryHackMe
---

# TryHackMe | Chocolate Factory

+++++++++++++++++++++++++++++++++++\
IP: 10.10.156.225\
Date: 07-12-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="523" alt="image" src="https://user-images.githubusercontent.com/115549820/206157845-70c0f767-e747-493b-a627-4e97aed4dad7.png">
  
**Open Ports**

21 - FTP - vsftpd 3.0.3\
22 - SSH - OpenSSH 7.6p1\
80 - Webserver - Apache httpd 2.4.29

### FTP Enumeration

<img width="642" alt="image" src="https://user-images.githubusercontent.com/115549820/206158810-82062e12-5fe8-4109-8b3b-4886001f2c44.png">

**gum_room.jpg**

<img width="507" alt="image" src="https://user-images.githubusercontent.com/115549820/206159918-15954d6d-e66c-40a6-b148-140e789c2a62.png">

<img width="302" alt="image" src="https://user-images.githubusercontent.com/115549820/206160382-613014b1-0426-4332-93d8-66ea938a2a1f.png">

<img width="302" alt="image" src="https://user-images.githubusercontent.com/115549820/206160711-c63a8ec7-d648-4d97-84d9-adab1ef922d2.png">

***b64.txt***

<img width="410" alt="image" src="https://user-images.githubusercontent.com/115549820/206160838-02ce732f-066b-4afb-9c3f-ca8c933a71a8.png">

<img width="410" alt="image" src="https://user-images.githubusercontent.com/115549820/206161509-50cbbafc-0bca-43c8-b18f-347468673556.png">

<img width="704" alt="image" src="https://user-images.githubusercontent.com/115549820/206161799-327c072e-df52-49b8-b37f-c1b33dcda885.png">

<img width="454" alt="image" src="https://user-images.githubusercontent.com/115549820/206166246-6f71743d-9110-44a7-9cf7-603d1ad530a0.png">


### Webserver Enumeration

<img width="480" alt="image" src="https://user-images.githubusercontent.com/115549820/206168188-66296dc0-0068-4904-b8d3-624d02592aa3.png">

**Index.html**

<img width="729" alt="image" src="https://user-images.githubusercontent.com/115549820/206167345-5e85523c-3c9b-4d75-b37c-d07aeab81ade.png">

**Home.php**

<img width="729" alt="image" src="https://user-images.githubusercontent.com/115549820/206167168-39a2ad02-175f-43ac-95a9-5c08bb30a92b.png">


## Fase 2: Getting Access

**Reverse Shell**

<img width="169" alt="image" src="https://user-images.githubusercontent.com/115549820/206169217-b752d70d-0f61-45c1-b58d-315a23b0d85c.png">

<img width="468" alt="image" src="https://user-images.githubusercontent.com/115549820/206180175-4a5a7deb-a20c-4114-9dab-19116e1842e9.png">

<img width="361" alt="image" src="https://user-images.githubusercontent.com/115549820/206183102-6e7832b2-524e-41bd-b8de-58d653a279d4.png">
  
## Fase 3: Intern Enumeration

<img width="320" alt="image" src="https://user-images.githubusercontent.com/115549820/206183277-cf0cb804-2b01-4f63-8857-f82a937cadf6.png">

<img width="320" alt="image" src="https://user-images.githubusercontent.com/115549820/206183528-775e05dd-d5c4-48d2-a506-825de44dccd6.png">

<img width="320" alt="image" src="https://user-images.githubusercontent.com/115549820/206183674-26960c3f-720b-4f29-bc31-b85d636ca0cb.png">

<img width="320" alt="image" src="https://user-images.githubusercontent.com/115549820/206183989-58e14572-bf69-47f5-bd64-9fdf20d9a15d.png">

<img width="320" alt="image" src="https://user-images.githubusercontent.com/115549820/206184919-7bc095ba-a583-4d5c-8b5f-b0cb370d9694.png">


  
## Fase 4: PrivEsc
  
## TryHackMe Questions
