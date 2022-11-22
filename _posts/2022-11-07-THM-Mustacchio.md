---
layout: post
title: TryHackMe | Mustacchio
---

# TryHackMe | Mustacchio

+++++++++++++++++++++++++++++++++++\
IP: 10.10.42.99\
Date: 07-11-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200538553-7331716c-f37e-4f71-a969-6238de3c019a.png">

**Open Ports**

22 - SSH - OpenSSH 7.2p2\
80 - Webserever - Apache 2.4.18\
8765 - Webserver - nginx 1.10.3

### Webserver Enumeration

**Dirbuster Output:80**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200342368-9cc68390-2205-431f-8c74-0adfac23ceb9.png">

***Homepage***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200342516-352272ab-55c5-4d61-b8bb-d411d0796213.png">

***/custom/js/users.bak**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200343128-30834348-da36-45e2-845a-1aa12bad9f8a.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200343515-e80d084c-b2da-4e90-a808-fae17aad5514.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200343857-fa496484-0e0f-4f6c-8c85-fbb0bc8a0823.png">

Possible cred:
> admin::bulldog19

**Dirbuster Output:8765**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200542525-564697fa-8e2c-4476-9b63-b79facc8e4bc.png">

***Homepage***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200542584-f6ea421d-d379-460c-a513-3e7b0a019f20.png">

***Admin Page***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200543376-7b6078f7-5215-441e-bc2a-6269d7af39c8.png">

***Source code AP***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200543552-4c64eaa7-1744-457d-aaed-f5c11bb89b08.png">

Possible username SSH:
> barry::??

***Dontforget.bak***

<img width="558" alt="image" src="https://user-images.githubusercontent.com/115549820/200545977-0851a40d-0c83-4437-bf28-b056b26e337d.png">


**Nikto Output**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200342329-02cda31b-386f-48e2-9c68-99a945772c34.png">

**XXE vuln**

https://book.hacktricks.xyz/pentesting-web/xxe-xee-xml-external-entity

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200559491-28cf7a2d-1045-4900-8b5b-f1d73268620f.png">

<img width="200" alt="image" src="https://user-images.githubusercontent.com/115549820/200559555-4289e657-b97f-4294-bf0d-a65097c83fed.png">

<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/200560093-114bb2bf-d1b4-4592-88a6-83924c95733e.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200560167-150ad20a-3c64-49fd-9233-87cad73e964b.png">

***Checking for barry SSH-key***

<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/200561266-65552f9b-7b5d-4024-b925-9777cbb0ba8f.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200561360-20b11bea-f009-4df3-bd20-63ed36b8c669.png">

***Cracking SSH password***

<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/200561903-048a779e-15ae-49bb-be6c-78278547c98f.png">

<img width="200" alt="image" src="https://user-images.githubusercontent.com/115549820/200562412-c65ce3ba-5ef2-46f3-ab47-d2bab2e3aadc.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200562599-abcfa191-4851-413b-af5e-635fe104e86e.png">

Credentials:
> barry::urieljames


## Fase 2: Getting Access

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200563001-f4071d09-7f1e-4f93-9b43-93112dbf77db.png">
  
## Fase 3: Intern Enumeration

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200564185-83dad356-a29d-4992-9e80-ea980fe027c9.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200565134-1f3256bb-5120-43c5-a8c2-b08b2de22a47.png">
  
## Fase 4: PrivEsc

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200565264-79b254b4-70cd-4446-9386-e58779228755.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200565492-9555fd38-6270-4952-98fd-f764d1d27048.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200565560-3559f3aa-a319-45ce-ae31-1d3859575815.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200565949-89a3662d-9bc6-4b7a-b5fe-19c0e313477c.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200567186-a98a22f7-130e-4533-99ec-24af4296e082.png">

<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/200567663-30610685-ba13-4fdf-8081-4338c8a2f406.png">


## TryHackMe Questions

user.txt
> 62d77a4d5f97d47c5aa38b3b2651b831

root.txt
> 3223581420d906c4dd1a5f9b530393a5
