---
layout: post
title: HackTheBox | Precious
categories: HackTheBox
---

# HackTheBox | Precious

+++++++++++++++++++++++++++++++++++\
IP: 10.10.11.189\
Date: 06-01-2023\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="450" alt="image" src="https://user-images.githubusercontent.com/115549820/210967185-ca577e6a-7d2d-44b8-a90a-dc109092b740.png">

**Open Ports**

22 - SSH - OpenSSH 8.4p1\
80 - HTTP - nginx 1.18.0\

### Webserver Enumeration

***Dirbuster output***

<img width="450" alt="image" src="https://user-images.githubusercontent.com/115549820/210976430-2898ba1c-ba1f-4681-b6c9-166a719aa244.png">

***Nikto output***

<img width="600" alt="image" src="https://user-images.githubusercontent.com/115549820/210973371-f48622e9-a6e1-4774-af93-67f8a2ed9656.png">

***Homepage***

<img width="750" alt="image" src="https://user-images.githubusercontent.com/115549820/210976612-969f1072-3930-434b-9159-f37b7c3e71ba.png">

<img width="750" alt="image" src="https://user-images.githubusercontent.com/115549820/210976939-536f5211-3a1f-4b04-bff1-3a23cf1f4313.png">

<img width="750" alt="image" src="https://user-images.githubusercontent.com/115549820/210978740-24b4a049-28c0-41e2-95a2-1abc3f67040c.png">


***Burpsuit***

<img width="750" alt="image" src="https://user-images.githubusercontent.com/115549820/210979232-455f67e8-0778-440f-a4fe-6cdb363c9d51.png">

***Uploading ruby shell***

<img width="650" alt="image" src="https://user-images.githubusercontent.com/115549820/210979450-236f482c-50e8-41b6-a5d6-2361479cc447.png">

<img width="350" alt="image" src="https://user-images.githubusercontent.com/115549820/210980221-bb2377e5-d87e-4380-9c7d-55b997c7171d.png">

<img width="640" alt="image" src="https://user-images.githubusercontent.com/115549820/210980478-e4e6aeac-97a8-4f77-9914-a456ab8c6e7c.png">

<img width="350" alt="image" src="https://user-images.githubusercontent.com/115549820/210980713-faf48e9c-0cda-49f4-ac3f-666ad5b31ff5.png">

***Shell???***



## Fase 2: Getting Access

  
## Fase 3: Intern Enumeration

  
## Fase 4: PrivEsc
  
## HackTheBox Questions
