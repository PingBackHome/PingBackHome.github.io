---
layout: post
title: TryHackMe | Startup
categories: TryHackMe
---

# TryHackMe | Startup

+++++++++++++++++++++++++++++++++++\
IP: 10.10.43.206\
Date: 21-12-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="430" alt="image" src="https://user-images.githubusercontent.com/115549820/208901811-f958762c-2b67-4517-ae7f-16027fbd05ca.png">

**Open Ports**

21 - FTP - vsftpd 3.0.3\
22 - SSH - OpenSSH 7.2p2\
80 - HTTP - Apache 2.4.18

### FTP Enumeration

<img width="425" alt="image" src="https://user-images.githubusercontent.com/115549820/208929786-7551e31c-c024-4198-abcf-e6f50ede874a.png">

***Files from FTP***

<img width="561" alt="image" src="https://user-images.githubusercontent.com/115549820/208914428-dcc217cd-bb34-403d-a30c-21786493b079.png">

<img width="594" alt="image" src="https://user-images.githubusercontent.com/115549820/208914551-b9a3486e-6ca0-426c-bdca-03b96ab49b04.png">

<img width="425" alt="image" src="https://user-images.githubusercontent.com/115549820/208916412-26525549-5525-4479-bc63-9c4b571e090f.png">

<img width="425" alt="image" src="https://user-images.githubusercontent.com/115549820/208929944-02f65a9d-6c20-420e-b37f-94eb6d7a363e.png">


### Webserver Enumeration

**Nikto output**



**Dirbuster output**

<img width="476" alt="image" src="https://user-images.githubusercontent.com/115549820/208930302-c3a97560-dea4-427c-a8bf-5e92ec14a8fc.png">

***Homepage***

<img width="633" alt="image" src="https://user-images.githubusercontent.com/115549820/208930478-57ada87b-3847-431a-bea1-a806021082b3.png">

***/files***

<img width="633" alt="image" src="https://user-images.githubusercontent.com/115549820/208930596-e92a677c-ff4d-4d24-b9a1-8c861c9a48ad.png">

## Fase 2: Getting Access

**Checking for upload capability on ftp server**

<img width="413" alt="image" src="https://user-images.githubusercontent.com/115549820/208931256-a5be73e5-72cc-4d0d-9255-31709eb1572b.png">

<img width="559" alt="image" src="https://user-images.githubusercontent.com/115549820/208931812-1211f34b-7d99-4f2b-8e1e-a6911edc357d.png">

<img width="559" alt="image" src="https://user-images.githubusercontent.com/115549820/208931964-d0479e0a-19f3-469c-b98e-e4fa448341eb.png">

***Uploading reverse php shell to ftp server***

<img width="1206" alt="image" src="https://user-images.githubusercontent.com/115549820/208932311-e4249ba6-079f-497e-8d80-e28e7c848ddb.png">

<img width="363" alt="image" src="https://user-images.githubusercontent.com/115549820/208932702-6eaf2052-0244-4200-bcad-c9b8236ac419.png">

<img width="564" alt="image" src="https://user-images.githubusercontent.com/115549820/208932751-a208fcc6-7cc2-409f-ba5c-e95aa8b7f4e5.png">

<img width="239" alt="image" src="https://user-images.githubusercontent.com/115549820/208932907-0f8b2a34-be89-4cc7-a847-04faed021465.png">

<img width="309" alt="image" src="https://user-images.githubusercontent.com/115549820/208932984-29d4fe66-9026-476e-b419-a4ff0b57be61.png">

<img width="547" alt="image" src="https://user-images.githubusercontent.com/115549820/208933079-8d844d6d-da00-4b79-b46d-27f292dfd1fb.png">


## Fase 3: Intern Enumeration

<img width="547" alt="image" src="https://user-images.githubusercontent.com/115549820/208933353-71a4078b-7538-4327-9c25-83a97a328ae7.png">

<img width="547" alt="image" src="https://user-images.githubusercontent.com/115549820/208933580-2808bd98-2690-4f1d-a1d8-54130dac810c.png">

<img width="547" alt="image" src="https://user-images.githubusercontent.com/115549820/208935350-8f54fba6-002f-451c-8e86-491df7ef9db5.png">

<img width="547" alt="image" src="https://user-images.githubusercontent.com/115549820/208935480-c4082458-6b93-4f0e-8e49-090bff97414f.png">

<img width="567" alt="image" src="https://user-images.githubusercontent.com/115549820/208935648-9e957f3e-1811-4ba9-b06e-5ad51071554b.png">

<img width="567" alt="image" src="https://user-images.githubusercontent.com/115549820/208935808-8753a3a8-eea0-40f5-a4aa-ced63afa9dab.png">

<img width="567" alt="image" src="https://user-images.githubusercontent.com/115549820/208936487-70308328-5dbe-4f7b-ad58-81d1a5553b86.png">

<img width="664" alt="image" src="https://user-images.githubusercontent.com/115549820/208936627-9a1d727f-ba08-40e0-bd60-09183393bb08.png">

<img width="790" alt="image" src="https://user-images.githubusercontent.com/115549820/208937501-77de6055-5dd3-4990-9ee2-2f37ea48f137.png">

<img width="790" alt="image" src="https://user-images.githubusercontent.com/115549820/208939512-eab34689-b126-40db-b67c-907ab6c20603.png">

> Possible creds:\
> lennie::c4ntg3t3n0ughsp1c3

<img width="404" alt="image" src="https://user-images.githubusercontent.com/115549820/208939959-96b44d0c-bfde-4fa6-8e66-65f7d02d38fb.png">

<img width="404" alt="image" src="https://user-images.githubusercontent.com/115549820/208940135-95f5022f-6c4f-487c-9808-e0189decc9e4.png">

## Fase 4: PrivEsc

**Inspecting scripting folder**

<img width="351" alt="image" src="https://user-images.githubusercontent.com/115549820/210219757-243b36d5-1e8e-483b-a0f8-9714abe571b8.png">

<img width="411" alt="image" src="https://user-images.githubusercontent.com/115549820/210219966-15f9e624-3437-4636-9995-2cf28cc44b70.png">

**Inspecting /etc/print.sh**

<img width="411" alt="image" src="https://user-images.githubusercontent.com/115549820/210220259-62a1c5ba-11c9-46de-b2e2-796767739478.png">

<img width="411" alt="image" src="https://user-images.githubusercontent.com/115549820/210220317-73db3b41-1d41-4d86-8bf8-f85191943fdd.png">

**Add reverse shell to print.sh**

<img width="1151" alt="image" src="https://user-images.githubusercontent.com/115549820/210220452-83318d22-902d-4068-8f5b-b061815a73fc.png">

<img width="575" alt="image" src="https://user-images.githubusercontent.com/115549820/210220570-8e043518-3394-4d65-ba6a-973cb4c1db3f.png">

<img width="148" alt="image" src="https://user-images.githubusercontent.com/115549820/210220634-d0771c75-0a9f-4af7-9fed-ca94ff1287f1.png">

<img width="410" alt="image" src="https://user-images.githubusercontent.com/115549820/210220807-5ae90775-77e5-4a21-9f90-0644b1b61520.png">

<img width="410" alt="image" src="https://user-images.githubusercontent.com/115549820/210220939-f28b936f-2298-4728-a7f5-544761199651.png">


## TryHackMe Questions

> user.txt\
> THM{03ce3d619b80ccbfb3b7fc81e46c0e79}

> root.txt\
> THM{f963aaa6a430f210222158ae15c3d76d}
