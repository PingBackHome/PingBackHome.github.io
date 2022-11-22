---
layout: post
title: TryHackMe | Ignite
---

# TryHackMe | Ignite

+++++++++++++++++++++++++++++++++++\
IP: 10.10.13.26\
Date: 24-10-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197513563-e47774a1-5ebb-4948-b795-b953cfe85709.png">

**Open Ports**

80 - Webserver - Apache 2.4.18

### Webserver Enumeration

**Homepage**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197514322-85bdce92-7637-480e-b5d7-8afb00f76c8b.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197514482-e28d699a-f1dc-4f57-b785-88a27a044ff0.png">

Credentials:
> admin::admin

**Dirbuster output**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197515220-b82b0f01-37c9-4178-86e4-1075b71ffda8.png">

**Nikto output**

<img width="1034" alt="image" src="https://user-images.githubusercontent.com/115549820/197522070-b1282073-2393-41b0-8924-b84f46905f43.png">


## Fase 2: Getting Access

**Finding exploit**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197518860-b88cfb98-3d43-48b1-91cd-8771c3f41371.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197521814-9955009b-4184-4c4f-8ff8-3321517306c0.png">

**Getting shell**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197521933-cea061c1-aba2-45e4-a60c-cba7101bf513.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197521987-3ce4d872-ad60-49b3-b3cb-2d4cfc4a0fc2.png">

***New clean shell***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197523498-17c8e388-3d69-40de-b338-754b6b187e28.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197523553-f5b40e9d-9e28-4f8c-b402-5ec167a2adae.png">

## Fase 3: Intern Enumeration

**Uploading linpeas.sh**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197524144-51516789-276b-4a04-a2f2-7d18de32d566.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197529188-849fcc0d-d819-4fc2-b524-a6342a7fe9d7.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197529429-9a95c0f8-ec9b-4333-99a4-49cec9786538.png">

> ?username?::mememe

  
## Fase 4: PrivEsc

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197530189-2ec234b2-9b3e-444f-87a3-9c49abae8288.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197526207-42d3f238-c4e2-4634-ae7a-29bf14f99bd2.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197530720-576c4e68-2ef7-438a-b717-b13cc2c9f377.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197530942-5209e8d6-00b1-479b-aba4-8592cb582b95.png">

Credentials:
> root::mememe

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197531321-971f429f-d19e-4c50-b139-a7bb8b51d341.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/197531436-907fb401-8421-4ccd-9d67-3dc61660b888.png">


## TryHackMe Questions

'User.txt'
> 6470e394cbf6dab6a91682cc8585059b

'Root.txt'
> b9bbcb33e11b80be759c4e844862482d 
