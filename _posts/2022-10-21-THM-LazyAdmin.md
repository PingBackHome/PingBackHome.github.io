---
layout: post
title: TryHackMe | LazyAdmin
---


# TryHackMe | LazyAdmin

+++++++++++++++++++++++++++++++++++\
IP: 10.10.47.71\
Date: 21-10-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scanning

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197149775-692777cb-8021-460e-8c56-d80f0199244f.png">


**Open Ports:**

22 -- SSH       -- OpenSSH 7.2p2
80 -- Webserver -- Apache 2.4.18


### Webserver Enumeration

**Home Page**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197150427-f69c3599-6a24-4bb9-b60d-15b156c99001.png">

**Nikto Scan**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197154938-ae6beecb-226d-4ad9-bc82-a5de31e398c1.png">

**Dirbuster Scan**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197157180-20f0dd93-a6fb-4789-bcd3-4d32f1da97fb.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197155959-051b53a1-3536-464f-bb89-fabafb99cb46.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197157265-19050bc1-22e7-414b-918f-6a942d4d8dc4.png">

***Result pages Dirb***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197157458-77472490-4728-47e5-bae7-94dc7c352dc3.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197157490-eedfff42-2dde-42e3-a056-62aee0209254.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197157569-ae2a4bdb-359d-4a90-8abd-cb758dec8f3a.png">

<img width="1031" alt="image" src="https://user-images.githubusercontent.com/115549820/197167270-6dfc6fe6-c765-42fc-9876-c56a8c803097.png">

***mysql_backup***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197157963-12d24ba3-d0df-4576-8177-ddfa3f600bd7.png">
<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197158585-1f83ec1c-38a3-4203-95ec-775e2e629d45.png">
<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197159218-e49cbdff-ccf2-4c0f-afcf-6f6d8ba86d6e.png">

Creds in sql backup:\
> manager::42f749ade7f9e195bf475f37a44cafcb\
> 42f749ade7f9e195bf475f37a44cafcb = md5 = Password123\
> admin::Password123


## Fase 2: Getting Access

### Search exploit

**Exploit DB**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197160418-eb6b1c41-26e8-41b9-9aad-1267663ff354.png">

SweetRice version: 1.5.1

**Shell upload**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197167630-11b464a4-041d-40d5-b3f6-38530fbaead5.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197168955-bc036add-a895-48c7-a27d-458f76cf8eb3.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197170664-79534761-0a52-46c7-924b-d4f242e8232b.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197170732-d25246df-d0a0-4f0a-84b1-d9cec699d793.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197170960-371557c8-f635-4200-b9fb-5586295867c2.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197171075-cd98bbbb-61b1-41ae-a5a2-72e2dbaee6d9.png">

No normal .php extention is accepted, try other format example: php1/2/3/4/5
<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197171160-0563817b-7ff6-47cd-9c73-88cea8371cbd.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197171502-d7dd730b-7f98-4fd2-b311-16fe91aef42e.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197171552-580844e0-1b17-47e7-a8ef-b88987117438.png">

<img width="927" alt="image" src="https://user-images.githubusercontent.com/115549820/197194523-f90bc145-4ed1-470a-ad9a-b638aa37decc.png">

## Fase 3: Intern Enumeration

<img width="927" alt="image" src="https://user-images.githubusercontent.com/115549820/197194707-eef0c406-5303-4ca5-9aba-240086229565.png">

<img width="311" alt="image" src="https://user-images.githubusercontent.com/115549820/197194907-5816697f-9170-4524-9051-6af982aa3e39.png">

**linpeas.sh**

<img width="468" alt="image" src="https://user-images.githubusercontent.com/115549820/197197007-27f87b7d-63dc-4874-b0f3-eba45c1bd549.png">

<img width="973" alt="image" src="https://user-images.githubusercontent.com/115549820/197197334-bbe3493d-7718-4022-b888-8c7613d80f63.png">


## Fase 4: PrivEsc

<img width="973" alt="image" src="https://user-images.githubusercontent.com/115549820/197197703-780fa6f3-9a08-4b50-9646-2a3fc69b0a3d.png">

<img width="659" alt="image" src="https://user-images.githubusercontent.com/115549820/197197936-4749d4e2-498b-4bd2-af84-282b068b23bb.png">

<img width="760" alt="image" src="https://user-images.githubusercontent.com/115549820/197198371-e4d9288e-bdce-4d08-93b7-6d4b47a757eb.png">



## TryHackMe Questions

'What is the user flag?'\
> THM{63e5bce9271952aad1113b6f1ac28a07}

'What is the root flag?'\
> THM{6637f41d0177b6f37cb20d775124699f}
