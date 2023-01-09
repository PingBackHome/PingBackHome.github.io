---
layout: post
title: HackTheBox | Soccer
categories: HackTheBox
---

# HackTheBox | Soccer

+++++++++++++++++++++++++++++++++++\
IP: 10.10.11.194\
Date: 09-01-2023\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="558" alt="image" src="https://user-images.githubusercontent.com/115549820/211281848-b99b34a4-729f-4277-98df-a0a4503dd2d7.png">

**Open Ports**

22 - SSH - OpenSSH 8.2p1\
80 - HTTP - Nginx 1.18.0\
9091 - xmltec - ??

### Webserver Enumeration

***Niktoscan output***

<img width="566" alt="image" src="https://user-images.githubusercontent.com/115549820/211290144-de521331-ce2e-4b77-84df-38eb61163d6a.png">

***Dirbuster output***

<img width="477" alt="image" src="https://user-images.githubusercontent.com/115549820/211290070-a5785d6b-641e-4999-9c9a-aef030de9d23.png">

***Homepage***

<img width="803" alt="image" src="https://user-images.githubusercontent.com/115549820/211290323-fe69bd22-9fdb-4f07-bda6-c671f1f9620c.png">

***/tiny***

<img width="803" alt="image" src="https://user-images.githubusercontent.com/115549820/211290470-e24eac92-6007-4589-927a-e635bae0af81.png">

***Login***

<img width="803" alt="image" src="https://user-images.githubusercontent.com/115549820/211290601-e5ec4e50-f13f-4519-aaa6-33354e1f3772.png">

<img width="803" alt="image" src="https://user-images.githubusercontent.com/115549820/211290896-e8f96f44-f689-4ff8-968a-f67c510386fa.png">

***/tinyfilemanager***

<img width="803" alt="image" src="https://user-images.githubusercontent.com/115549820/211291129-0db4d139-4508-4743-b195-7592e18d5f69.png">

## Fase 2: Getting Access

***Uploading shell***

<img width="795" alt="image" src="https://user-images.githubusercontent.com/115549820/211293190-46bd808c-5abf-4312-8231-ef7b1c9f5bbb.png">

<img width="795" alt="image" src="https://user-images.githubusercontent.com/115549820/211293257-422b296f-d338-4aef-9e02-fb99b9d8def7.png">

<img width="378" alt="image" src="https://user-images.githubusercontent.com/115549820/211294881-0067ec7b-c1ea-49cf-a217-ca145a0fdeaa.png">

<img width="795" alt="image" src="https://user-images.githubusercontent.com/115549820/211293478-e873e88f-390d-470b-b601-0fb32b46366a.png">

***Acces***

<img width="795" alt="image" src="https://user-images.githubusercontent.com/115549820/211294197-f0d226bc-02be-462c-8189-44d1ad70fb9e.png">

<img width="378" alt="image" src="https://user-images.githubusercontent.com/115549820/211295028-ca9ac55b-719a-44f0-a864-1815758d0b13.png">

<img width="542" alt="image" src="https://user-images.githubusercontent.com/115549820/211295258-8306fd45-c7a5-4606-a568-2bbb1b469b6a.png">

  
## Fase 3: Intern Enumeration

  
## Fase 4: PrivEsc
  
## HackTheBox Questions
