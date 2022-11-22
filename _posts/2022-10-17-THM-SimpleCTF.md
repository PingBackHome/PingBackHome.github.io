---
layout: post
title: TryHackMe | Simple CTF
---

# TryHackMe | Simple CTF

+++++++++++++++++++++++++++++++++++\
IP: 10.10.12.132\
Date: 17-10-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196174233-546702ef-6f54-4c39-bf3a-2bebcd2dbee6.png">

**Open Ports**

21      FTP        - vsftpd 3.0.3\
80      Webserver  - Apache 2.4.18\
2222    SSH        - OpenSSH 7.2p2

### FTP Enumeration

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196178694-6f05a0a3-5ddd-48dc-b2e2-dcccba0d2e4b.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196178945-2c29d8d8-0dec-4f4b-a01a-459eb76bcc25.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196179043-06b24b4a-dfd9-4971-bb98-c4d801a438c6.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196179255-b77a218f-64ba-45c7-9ed1-bfacf488033d.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196179581-adba8fef-6b8b-41e5-a1d2-351afcc6047e.png">


### Webserver Enumeration

**Dirbuster Scan**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196182130-bbf24673-3e97-4ff0-93dc-865a0869aa1c.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196181966-ca86ee8e-0586-4a6c-8246-8e61807e9ad3.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196182246-1d695ff2-117a-44de-a06d-416703aae4fd.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196182327-8c1831a2-efac-43e1-a3b2-79c43f398459.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196182497-c4cb7041-1958-4949-8b7b-426f82d798b3.png">


**Finding CVE**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196184055-830af94a-29cb-4230-9678-ec69b71792d2.png">

**Nikto Scan**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196186110-e8bbc756-ec9d-4093-b905-b40f72fc7e44.png">

**Creds**

> Username(s):
> > mitch

## Fase 2: Getting Access

**Exploit with CVE**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196188518-117e11be-30b4-4591-95c1-36158b72d3e3.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196190471-3b599647-3cf6-4502-9b49-f1d915d95290.png">

**Cracking Password with hashcat**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196191921-e079f1dd-6c45-429f-8f48-db848908330f.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196191993-5ffca4a5-5a9d-49d4-a32a-08ed4291939f.png">


**Hydra**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196190128-78ada73b-98bf-4c6a-a336-063dd5460e5f.png">

**Password(s)**

>mitch::secret

## Fase 3: Intern Enumeration

**Uploading linpeas.sh**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196193863-e58799cd-a706-4faa-ad96-8a9af7fdea37.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196194154-58fbe0b3-7233-4ab1-9692-e44278bad29d.png">


**Running linpeas.sh**

<img width="250" alt="image" src="https://user-images.githubusercontent.com/115549820/196194280-7720915f-7b51-4933-ac9d-d6b67cdc6064.png">



**Output linpeas.sh**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196196068-94018aeb-c09e-4851-a116-b01671ea3952.png">


## Fase 4: PrivEsc

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196199117-898ed3a7-94e0-4aea-8481-cb98a5bcb25c.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196199208-63d98b1a-e460-4090-bcb4-9672f68e7245.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196199333-94894948-94ea-436b-9a33-a8e19f5becc2.png">


## TryHackMe Questions

'How many services are running under port 1000?'
> 2

'What is running on the higher port?'
> SSH

'What's the CVE you're using against the application?'
> CVE-2019-9053

'To what kind of vulnerability is the application vulnerable?'
> SQLI

'What's the password?'
> Secret

'Where can you login with the details obtained?'
> SSH

'What's the user flag?'
> G00d j0b, keep up!

'Is there any other user in the home directory? What's its name?'
> Sunbath

'What can you leverage to spawn a privileged shell?'
> VIM

'What's the root flag?'
> W3ll d0n3. You made it!
