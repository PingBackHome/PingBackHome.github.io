---
layout: post
title: TryHackMe | Cyborg
categories: TryHackMe
---

# TryHackMe | Cyborg

+++++++++++++++++++++++++++++++++++\
IP: 10.10.84.219\
Date: 12-12-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

![image](https://user-images.githubusercontent.com/115549820/207075959-8e575fad-bd33-41c2-9d26-51db02e12921.png)

**Open Ports**

22 - SSH - OpennSSH 7.2p2\
80 - Webserver - Apache 2.4.18

### Webserver Enumeration

***Landing page***

![image](https://user-images.githubusercontent.com/115549820/207077137-6744188f-ccf4-4483-a5bb-ff3244eb3eb1.png)

**Dirbuster output**

![image](https://user-images.githubusercontent.com/115549820/207078470-d2a6032c-f8b7-4c87-ab4f-4b67dc4a2bc4.png)

***/admin***

![image](https://user-images.githubusercontent.com/115549820/207079826-4f678ffb-84ca-46e5-9696-2648bb4815c8.png)

***/admin/archive.tar***

![image](https://user-images.githubusercontent.com/115549820/207082804-9b27be94-ec99-4d67-85a1-5d9f258d7f89.png)

https://borgbackup.readthedocs.io/en/stable/installation.html

![image](https://user-images.githubusercontent.com/115549820/207084264-f1a02dcd-bee7-4c51-8674-5758235bf757.png)

![image](https://user-images.githubusercontent.com/115549820/207084455-20d1d3b5-c836-439a-aca8-61b977793e2b.png)

![image](https://user-images.githubusercontent.com/115549820/207084862-9e420cb6-8d60-45b9-a856-9058fdb3b1a6.png)

![image](https://user-images.githubusercontent.com/115549820/207086031-4e781b98-64e2-4e9f-8b33-a2c9f5374f47.png)

![image](https://user-images.githubusercontent.com/115549820/207086135-ee2358d1-a117-4d6d-8d42-002a2ad849a7.png)

![image](https://user-images.githubusercontent.com/115549820/207086291-d7463fa8-98e0-44fe-aba2-c2b90343aaaf.png)

![image](https://user-images.githubusercontent.com/115549820/207086408-dfdbbc6e-f077-4eff-8474-5f92a311ad7a.png)

![image](https://user-images.githubusercontent.com/115549820/207086630-64a6d714-848a-4e6d-9c57-88310a945e2e.png)

![image](https://user-images.githubusercontent.com/115549820/207086898-93a22ddf-6d0f-43a9-9b1b-c1a88d365a29.png)

> Cred:\
> alex::S3cretP@s3

***/etc/squid/passwd***

![image](https://user-images.githubusercontent.com/115549820/207080023-c7b36314-6d48-4b86-a2c3-ce2dec78d122.png)

![image](https://user-images.githubusercontent.com/115549820/207080311-ccaf1aa3-6c17-4b1d-81e5-d89ab03f352d.png)

![image](https://user-images.githubusercontent.com/115549820/207080466-774acfb7-151e-4f4f-b206-f65b4cb37e18.png)

![image](https://user-images.githubusercontent.com/115549820/207080817-f034af2f-b338-484c-bdfb-355222247445.png)

![image](https://user-images.githubusercontent.com/115549820/207081502-7950f03c-dfdd-4d70-9c08-5e28230723ac.png)

![image](https://user-images.githubusercontent.com/115549820/207081702-a76743a3-1a17-434d-9840-516121a658df.png)

> Creds:\
> music_archive::squidward

***/etc/squid/squid.conf***

![image](https://user-images.githubusercontent.com/115549820/207079992-9c22cfd3-9ee3-4913-919d-f195892791af.png)


## Fase 2: Getting Access

![image](https://user-images.githubusercontent.com/115549820/207087897-b83167ed-0fe1-47e0-b5c9-7a2187defbc3.png)
  
## Fase 3: Intern Enumeration

![image](https://user-images.githubusercontent.com/115549820/207088107-52781c5a-daea-4e2d-81d5-46f654767b17.png)

![image](https://user-images.githubusercontent.com/115549820/207088202-546ff47a-da88-447d-b890-7876f253fbb7.png)

![image](https://user-images.githubusercontent.com/115549820/207088557-bbd93218-10df-40b2-9be3-efe4af04f20e.png)

![image](https://user-images.githubusercontent.com/115549820/207088644-6ccdbc9c-9a9b-45e8-87c5-7ac8e2540558.png)

  
## Fase 4: PrivEsc

![image](https://user-images.githubusercontent.com/115549820/207089046-0b3c577b-b9d8-4ef5-94f5-729a9eb044e6.png)

![image](https://user-images.githubusercontent.com/115549820/207089982-0f435e94-51b3-437c-9094-2893112e6b8c.png)

![image](https://user-images.githubusercontent.com/115549820/207090064-6f1f97ed-052c-44e0-bf53-bd3798e08195.png)

![image](https://user-images.githubusercontent.com/115549820/207090372-046656b5-dfb6-424a-ad87-da97f379ccde.png)

![image](https://user-images.githubusercontent.com/115549820/207090463-36d4a45f-95cf-4cd0-be7e-e61c43bf0afe.png)

![image](https://user-images.githubusercontent.com/115549820/207091269-3bbbaa45-7beb-4d9a-89dc-c53e27f0034a.png)

![image](https://user-images.githubusercontent.com/115549820/207091357-e3458a27-0656-4fc0-86ca-4785b621dc4c.png)

![image](https://user-images.githubusercontent.com/115549820/207093144-3bb23fcc-ba4e-4495-9f5e-827d1b125017.png)

![image](https://user-images.githubusercontent.com/115549820/207093194-e6a6955d-3930-4f63-9aa2-322fd2b5aaf1.png)



## TryHackMe Questions

Scan the machine, how many ports are open? 
> 2

What service is running on port 22?
> SSH

What service is running on port 80?
> HTTP

What is the user.txt flag?
> flag{1_hop3_y0u_ke3p_th3_arch1v3s_saf3}

What is the root.txt flag?
> flag{Than5s_f0r_play1ng_H0p£_y0u_enJ053d}
 
 
