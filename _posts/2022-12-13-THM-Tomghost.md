---
layout: post
title: TryHackMe | TomGhost
categories: TryHackMe
---

# TryHackMe | TomGhost

+++++++++++++++++++++++++++++++++++\
IP: 10.10.74.159\
Date: 13-12-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

![image](https://user-images.githubusercontent.com/115549820/207422042-71bdf0d0-e83d-4f6b-9f74-81c04d4e4927.png)
  
**Open Ports**

22 - SSH - OpenSSH 7.2p2\
53 - tcpwrapped - ?\
8009 - Apache Jserv (Protocol v1.3)\
8080 - Webserver - Apache Tomcat 9.0.30

### Webserver Enumeration

***Landing page***

![image](https://user-images.githubusercontent.com/115549820/207423027-3c95a77e-f715-4b08-9139-340f1610e460.png)

<img width="1111" alt="image" src="https://user-images.githubusercontent.com/115549820/207598769-67c85de2-c7eb-4eaa-ba27-613cb58465e2.png">

***Searchsploit***

<img width="541" alt="image" src="https://user-images.githubusercontent.com/115549820/207601461-9c9c0d46-f47a-4165-89f2-a13f9bf5c8a5.png">

<img width="431" alt="image" src="https://user-images.githubusercontent.com/115549820/207601634-31fa659d-0245-4ee7-ab1a-41919c0c5436.png">

<img width="431" alt="image" src="https://user-images.githubusercontent.com/115549820/207603838-de1a7bf8-e06b-4221-9960-e282400db911.png">

https://github.com/Hancheng-Lei/Hacking-Vulnerability-CVE-2020-1938-Ghostcat/blob/main/CVE-2020-1938.md

<img width="431" alt="image" src="https://user-images.githubusercontent.com/115549820/207605087-f7270e7b-3682-4df5-bbbe-07221cbefd62.png">

> Credentials:
> skyfuck::8730281lkjlkjdqlksalks


## Fase 2: Getting Access

<img width="431" alt="image" src="https://user-images.githubusercontent.com/115549820/207605597-bd3ad88f-648d-4220-98b1-dc46e0396749.png">

  
## Fase 3: Intern Enumeration

<img width="431" alt="image" src="https://user-images.githubusercontent.com/115549820/207605723-4f948a85-7bbd-4109-8668-b81301252fa9.png">

<img width="431" alt="image" src="https://user-images.githubusercontent.com/115549820/207606555-303f355f-6805-4078-b7a1-2101dae51001.png">

<img width="545" alt="image" src="https://user-images.githubusercontent.com/115549820/207606603-728c71c2-682c-4202-87b2-8e5cdf011a21.png">

<img width="545" alt="image" src="https://user-images.githubusercontent.com/115549820/207606882-c919af8a-bbe1-420f-a8dc-463f11be1c09.png">

<img width="545" alt="image" src="https://user-images.githubusercontent.com/115549820/207607090-98412d96-ccca-43c4-81f4-d8b9b6981f71.png">

<img width="567" alt="image" src="https://user-images.githubusercontent.com/115549820/207607737-f2309c2e-20ef-4089-bfde-c153a8f8c731.png">

<img width="567" alt="image" src="https://user-images.githubusercontent.com/115549820/207607862-6a464712-fdaa-48f4-98be-1320cff85d99.png">

<img width="567" alt="image" src="https://user-images.githubusercontent.com/115549820/207608383-d2a6c9cd-cac6-43e4-a5f7-1767025d5b34.png">

> Credential:
> merlin::asuyusdoiuqoilkda312j31k2j123j1g23g12k3g12kj3gk12jg3k12j3kj123j

<img width="567" alt="image" src="https://user-images.githubusercontent.com/115549820/207608612-38e44e65-9577-4f1c-b4bb-c18b084140fe.png">

<img width="567" alt="image" src="https://user-images.githubusercontent.com/115549820/207608738-d9ca35b4-de7d-473d-afc1-7b54d932adbe.png">

<img width="239" alt="image" src="https://user-images.githubusercontent.com/115549820/207608868-30c27764-7074-4e6b-966a-a20e9a78415a.png">
  
## Fase 4: PrivEsc

<img width="472" alt="image" src="https://user-images.githubusercontent.com/115549820/207609048-470de4ea-685e-4b32-8edc-e5a733d704fa.png">

<img width="759" alt="image" src="https://user-images.githubusercontent.com/115549820/207609685-a0592228-5032-4614-8658-06f5c4d792c7.png">

<img width="566" alt="image" src="https://user-images.githubusercontent.com/115549820/207609798-f345a8df-2d3a-4fd5-8a0a-e2944d990dc1.png">

<img width="566" alt="image" src="https://user-images.githubusercontent.com/115549820/207609885-638a2873-3e4f-4842-a763-188b846c3acd.png">

## TryHackMe Questions

user.ttx
> THM{GhostCat_1s_so_cr4sy}

root.txt
> THM{Z1P_1S_FAKE}
