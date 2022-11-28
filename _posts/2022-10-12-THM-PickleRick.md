---
layout: test
title: TryHackMe | Pickle Rick
---

# TryHackMe | Pickle Rick

+++++++++++++++++++++++++++++++++++\
IP: 10.10.171.24\
Date: 12-10-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scanning

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/195342710-e2607866-92fc-43d0-942b-dfc15a857699.png">

**Open Ports:**

22    SSH         - OpenSSH 7.2p2\
80    Webserver   - Apache 2.4.18\

### Webserver Enumeration

**Home Pages**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/195343454-0b611152-0ce2-4ce9-8d24-f21dfcb527d7.png">

**Home Page Source Code**

<img width="250" alt="image" src="https://user-images.githubusercontent.com/115549820/195343706-65744c5f-476c-4dee-8018-54bb0de19791.png">

>Username: R1ckRul3s

**Nikto Scan**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/195345488-ee1fd010-59b3-41e9-90d7-cebd81ba7a62.png">

**Dirbuster Scan**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/195345111-a80855b4-59c4-490f-a5a8-1976588a398d.png">

**Results Web Enumeration**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/195345780-a306b3c8-67bf-47db-bedf-d8049eaeb6bf.png">


<img width="522" alt="image" src="https://user-images.githubusercontent.com/115549820/195347190-3f75e059-f166-4962-8b4c-710fa1ff52a4.png">

## Fase 2: Getting Access

**Hydra ssh cracking**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/195347763-c71a26dd-286c-41ca-8551-fd1e7f30a115.png">

**Login at webportal**

>Username: R1ckRul3s\
>Password: Wubbalubbadubdub

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/195348182-b14ed1b3-27a1-4322-9a23-9eafa44d78e3.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/195348386-8e83faa2-01a5-4740-a07a-baf81cc66441.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/195348819-b25e638c-e53e-4768-8667-dcd99d6746e3.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/195350051-5631c1e9-7e7f-4987-8caf-0e6e09fa6cde.png">

<img width="260" alt="image" src="https://user-images.githubusercontent.com/115549820/195350600-384b633d-355f-4241-8028-b0fc69420586.png">

<img width="293" alt="image" src="https://user-images.githubusercontent.com/115549820/195352009-65f817f3-a6e7-4b8e-86e0-9c37c7040354.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/195357084-276f30f5-358e-48a0-a4c1-992d5d76054f.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/195357551-eeff30e2-4ac0-4a7d-a956-498f7d848646.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/195358537-33d87000-b5b9-4868-9626-0b42d61cca08.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/195358605-fa7fff5a-16e2-406f-bbae-86af8696a77a.png">

<img width="399" alt="image" src="https://user-images.githubusercontent.com/115549820/196170395-8da17a38-6300-414a-a01f-ec3268efd442.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196170266-c3252114-aa8c-4f19-be96-7c6485677112.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196171118-ca4ff4df-cc55-4837-8221-8918d4cbb922.png">




