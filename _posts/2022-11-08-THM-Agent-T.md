---
layout: post
title: TryHackMe | Agent T
categories: TryHackMe
---

# TryHackMe | Agent T

+++++++++++++++++++++++++++++++++++\
IP: 10.10.131.39\
Date: 08-11-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="250" alt="image" src="https://user-images.githubusercontent.com/115549820/200572843-a5816ec5-3640-44c0-b00b-2110e7e45a73.png">

**Open Ports**

80 - Webserver - PHP cli server 5.5


### Webserver Enumeration

**Nikto Output**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200577678-a0df87ac-4148-4bba-af6c-a00e842501a3.png">

**Dirbuster Output: common**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200574281-03b8405d-7908-4e63-98b8-8b671ee7b711.png">

**Dirbuster Output: small**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/200577574-81823c56-200b-4dc4-8a0a-cf802837d044.png">


## Fase 2: Getting Access

https://github.com/flast101/php-8.1.0-dev-backdoor-rce/blob/main/revshell_php_8.1.0-dev.py

<img width="250" alt="image" src="https://user-images.githubusercontent.com/115549820/200578404-4ecc87a1-c332-4be8-9687-bf63bd3687d3.png">

<img width="700" alt="image" src="https://user-images.githubusercontent.com/115549820/200580776-9fd2b967-e429-4b9e-9e02-9e02629ea97a.png">

<img width="197" alt="image" src="https://user-images.githubusercontent.com/115549820/200581073-cdfe4965-7426-48ec-86ef-d9934c25e952.png">

<img width="439" alt="image" src="https://user-images.githubusercontent.com/115549820/200581199-a8adf67a-7374-45cf-9b0b-96790b21f3de.png">

<img width="507" alt="image" src="https://user-images.githubusercontent.com/115549820/200581273-2e9ab1ce-6fcc-4f1d-9473-5940742f8aff.png">
  
## Fase 3: Intern Enumeration

<img width="507" alt="image" src="https://user-images.githubusercontent.com/115549820/200581499-539bd1b9-d6c9-4cc3-a5fb-ffb23cf39259.png">

  
## Fase 4: PrivEsc

-

## TryHackMe Questions

What is the flag?
> flag{4127d0530abf16d6d23973e3df8dbecb}
