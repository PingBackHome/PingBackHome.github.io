---
layout: post
title: TryHackMe | Agent Sudo
categories: TryHackMe
---

# TryHackMe | Agent Sudo

+++++++++++++++++++++++++++++++++++\
IP: 10.10.191.235\
Date: 19-10-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scanning

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196645543-b5c95102-a68d-4b08-b929-449fddc41afa.png">

**Open Ports:**

21  -- FTP        -- vsftp 3.0.3\
22  -- SSH        -- OpenSSH 7.6p1\
80  -- Webserver  -- Apache 2.4.29


### Webserver Enumeration

**Home Pages**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196646679-6bf2e288-b5ce-4ad4-96b1-78429baaee8c.png">

**Change user-agent**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196658918-b0af44e7-9fd7-4fad-8420-8042979a4708.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196658989-17d07ad9-2369-4de3-9858-b41e37957c4b.png">

***Payload letters a-z***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196659428-b1fc8b45-249e-4454-a40c-ba98fbb228d3.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196659591-54022182-96d4-4aac-b7a8-819d931b93fc.png">

***Payload letters A-Z***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196660063-ce711f14-b6c1-4703-a0b9-48522c0f2f3a.png">

***Result agent: C***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196660473-1144276e-9eb4-43e0-b665-70f3bcc5905d.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196660577-3f9a96a0-65e2-4088-83f3-ae5d9db09b2f.png">


***Result agent: R***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196660777-1c97e252-7459-4e5c-921a-a9086c8740d2.png">

**Nikto Scan**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196661142-2da4727f-4ccc-4799-ba84-c496b4871e74.png">

**Dirbuster Scan**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196661255-c170f2b9-dbf2-4f7f-902b-8386fb27dd4e.png">

### FTP Enumeration

***Nmap script***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196669990-0cd79d63-2194-489b-877e-59511ceb6dee.png">

## Fase 2: Getting Access

**FTP Cracking w/ Hydra**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196671057-deea60d5-28e7-4fd6-9bb8-c7c5666dffe2.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196671383-11ed3361-a4b8-4f6a-993f-80fb682ddc37.png">

**FTP server**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196671773-c1e93602-1fba-458b-af27-7f8b6a7ed9ed.png">

***Message: To_agentJ.txt***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196671952-c46277d0-277e-424b-8f3b-7a7489211671.png">

***Finding Password in Pictures***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196673166-82ea97a3-efd1-4ebc-a6ff-a622ffce4fb9.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196673083-3b5a1da4-069b-479b-9975-02d19952e22b.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196673396-e72b93cb-691d-476d-8787-ee277f52e0c8.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196673489-fa299efa-f0a6-4613-98d7-c6b9ab8ef5f5.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196673625-a93b0b9a-f423-4946-bd88-cc68f2c04669.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196673781-ec11f1ff-9d45-4a57-bd44-fd740de23be7.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196674051-e9b1818f-1ff4-4d18-8efb-e474761599ac.png">

***Crack zip file***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196674373-dff8ad18-c20e-45d6-bbf6-da37fe4d9bbb.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196674731-0739dcd6-8067-49f7-bb8f-c7cd2f41c574.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196674859-1cdd5c08-8f51-4748-85e6-07652a02dbe5.png">

***Steghide cute-alien.jpg***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196676602-32b78008-b3b3-4194-8d19-d9de3117349a.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196676989-2ea508bd-6345-4c13-ba7c-a1e6c4831232.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196677098-77632d18-93a1-441a-931e-0315712a572f.png">

***Collected Creds***

> Chris::crystal\
> James::hackerrules!


## Fase 3: Intern Enumeration

***Uploading linpeas.sh***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196678551-d2652f79-bee9-45ee-925f-eb3c2ccaea6c.png">

***linpeas results***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196679849-70fea085-1058-4388-a481-21cb68ff926b.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196680774-b2666aed-6d47-4dda-975f-319a0736ad1f.png">

***Alien_autospy.jpg***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196681618-fced8b0e-2299-4357-8f4b-987471513b6b.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196682418-abf0ca66-32d3-4775-adb5-1e35f7674a58.png">


## Fase 4: PrivEsc

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196682561-8edbd449-cc5a-42cd-acf0-4dd46d1b8e37.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196682790-8fb1dcf4-f47f-400b-88f9-f854e0e18f79.png">

***CVE-2021-4034***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196683977-bd9f7c5c-dda2-4549-8f8a-55880bb1e058.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196683898-f9b52a5b-a57f-409d-94b6-e52ea5fccc36.png">

Doesn't work.... :(

***Sudo exploit***

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196688721-65f07548-dcef-4777-b259-2d0ecb0a1a3c.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196688835-2cdab7f4-99e5-4c42-a1d5-0ee97a6e3891.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196689072-3dc9d5f7-d3b3-434e-b187-da1971e6607d.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196689322-85e394c0-64bb-4441-ad3f-124d48429896.png">


## TryHackMe Questions

'How many open ports?'
> 3

'How you redirect yourself to a secret page?'
> user-agent

'What is the agent name?'
> Chris

'FTP password'
> Crystal

'Zip file password'
> Alien

'Steg password'
> Area51

'Who is the other agent?'
> James

'SSH password'
> Hackerrules!

'What is the user flag?'
>b03d975e8c92a7c04146cfa7a5a313c7

'What is the incident of the photo called?'
> Roswell alien autospy

'CVE number for escalation?'
> CVE-2019-1487

'What is the root flag?'
> b53a02f55b57d4439e3341834d70c062

'(Bonus) Who is Agent R.?'
> Deskel

