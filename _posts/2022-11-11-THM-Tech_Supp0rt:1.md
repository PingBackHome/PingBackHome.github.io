---
layout: post
title: TryHackMe | Tech_Support:1
---


# TryHackMe | Tech_Supp0rt: 1

+++++++++++++++++++++++++++++++++++\
IP: 10.10.148.163\
Date: 11-11-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201313475-6d329c2a-29a1-4d7f-b814-36fe8b61cb07.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201314084-c987de5e-0ce2-476b-8a38-cad4b7ccfb86.png">

**Open Ports**

22 - SSH - OpenSSH 7.2p2\
80 - Webserver - Apache 2.4.18\
139 - SMB - Samba\
445 - SMB - Samba

### Webserver Enumeration

**Nikto Output**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201315997-1da04460-6769-4bc3-9c63-833eddc4503f.png">

**Dirbuster output**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201316118-a3b5680a-9fad-4037-85ea-e556c6fdd8a8.png">

***Dirbuster /subrion***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201323878-5f6af11f-0152-4609-a7af-fde5e260fc6d.png">

**wpscan output**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201321722-1c956e7f-9c6a-4557-ac8a-a24f83324b44.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201321582-a0d87b9c-cc83-463d-89db-e04ced23c1c5.png">

Possible creds
> support::??

***wpscan passwordspray***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201345891-9a8455b3-50ba-44e4-ad38-50b9b59735a8.png">

**/subrion/panel**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201348497-ed6bf2d2-fa9c-4728-bbd7-e37b67242b13.png">

***Subrion version***

<img width="350" alt="image" src="https://user-images.githubusercontent.com/115549820/201339715-8fe2a18c-9a6e-44ca-89d1-83ef17158b11.png">


### SMB Enumeration

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201317738-d7f81fbc-355d-43b7-bbb5-0ef14b91b5ef.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201317868-6a756e15-d9e4-4afc-b97f-cc8638d81d4c.png">

**enter.txt**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201318407-1a2ff939-fee8-4f05-a3fa-d0e8ff86e105.png">

Credential for subrion
> admin::Scam2021


## Fase 2: Getting Access

**Possible exploitation**

> Wordpress 5.7.2\
> Subrion 4.2.1

**Subrion exploitation**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201340172-7d8ce0e9-5565-498c-98ee-21e047372261.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201340521-ce6cac20-5b75-4def-8765-a494122ddc9a.png">

<img width="350" alt="image" src="https://user-images.githubusercontent.com/115549820/201340700-9d4057ad-409f-4cbb-b1f2-31c2b728c088.png">

***Getting shell***

<img width="631" alt="image" src="https://user-images.githubusercontent.com/115549820/201341682-2664730e-ba65-4816-9e8f-ab67d2186cc1.png">

## Fase 3: Intern Enumeration

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201342763-e4579429-b120-4795-a793-28e8553ec5ff.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201342828-bdd1af62-83fd-4b26-a227-37a4d689af18.png">

MySQL/Wordpress creds
> support::ImAScammerLOL!123!

**Clean shell in subrion**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201345733-f5712d19-6733-4b1a-89e9-986cd060c957.png">

<img width="650" alt="image" src="https://user-images.githubusercontent.com/115549820/201346443-32b80c04-1e03-4e38-9baa-6f5f9e42e356.png">

<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/201346618-7c601b53-036a-42f6-b7ac-c93eb742b795.png">

<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/201347509-e916c7d6-5376-4862-b57f-7dbffd71b643.png">

<img width="550" alt="image" src="https://user-images.githubusercontent.com/115549820/201347660-fbb03a54-0113-4523-b3d6-2c2a3f29d29f.png">

  
## Fase 4: PrivEsc

<img width="750" alt="image" src="https://user-images.githubusercontent.com/115549820/201347787-0d96d6f6-4f98-40ec-82a3-59642b4761dd.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201348099-9295968e-6c10-4376-a822-04ec447e483a.png">


## TryHackMe Questions


What is the root.txt flag?
> 851b8233a8c09400ec30651bd1529bf1ed02790b
