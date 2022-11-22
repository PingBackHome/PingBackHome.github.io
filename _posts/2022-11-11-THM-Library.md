---
layout: post
title: TryHackMe | Library
---

# TryHackMe | Library

+++++++++++++++++++++++++++++++++++\
IP: 10.10.120.182\
Date: 11-11-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201355237-2ef10e23-d129-4629-b35e-58796f4a3f75.png">

**Open Ports**

22 - SSH - OpenSSH 7.2p2
80 - Webserver - Apache 2.4.18

### Webserver Enumeration

**Nikto Output**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201359520-adc7a76c-dce2-4eb2-8859-6a5aeff94e9a.png">

**Dirbuster Output**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201361234-17681e93-28d1-42b7-8068-041c7427ae56.png">

***Robots.txt***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201361328-06870767-c01c-4d53-b539-22040d03f15e.png">

***Homepage***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/201361498-59b8e257-72b2-44fa-9d46-7ec5a10780d1.png">

Possible username:
> meliodas 


## Fase 2: Getting Access

**SSH cracking w/ Hydra**

<img width="550" alt="image" src="https://user-images.githubusercontent.com/115549820/201363124-16b14a02-2f12-4bb3-8b8a-e13271a402cd.png">

<img width="550" alt="image" src="https://user-images.githubusercontent.com/115549820/201363308-65f9fed8-cc96-4720-95d2-506697ed7748.png">

Creds:
> meliodas::iloveyou1

  
## Fase 3: Intern Enumeration

<img width="450" alt="image" src="https://user-images.githubusercontent.com/115549820/201363535-8400286e-9beb-4b64-be62-6cd796a9062a.png">

<img width="700" alt="image" src="https://user-images.githubusercontent.com/115549820/201363621-f5399e71-feaa-4080-ba16-1d46318340eb.png">

## Fase 4: PrivEsc

<img width="450" alt="image" src="https://user-images.githubusercontent.com/115549820/201366289-890d1c71-6edd-414f-8247-b12a6a36023a.png">

<img width="150" alt="image" src="https://user-images.githubusercontent.com/115549820/201366035-3ca2c225-3d30-4eca-80bd-b19a7e0ce42b.png">


<img width="770" alt="image" src="https://user-images.githubusercontent.com/115549820/201365766-04d9d46f-75b1-4594-adf6-3c9f9c2355c6.png">

## TryHackMe Questions

user.txt
> 6d488cbb3f111d135722c33cb635f4ec

root.txt
> e8c8c6c256c35515d1d344ee0488c617
