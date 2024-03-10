---
layout: post
title: HackTheBox | Stocker
categories: THM
---

# HackTheBox | Stocker

+++++++++++++++++++++++++++++++++++\
IP: 10.10.11.196\
Date: 23-01-2023\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="461" alt="image" src="https://user-images.githubusercontent.com/115549820/214052665-a62d4496-f4ec-4e3d-9171-7bd983d96f8b.png">

**Open Ports**

22 - SSH - OpenSSH 8.2p1\
80 - HTTP - nginx 1.18.0

**Edit host file for redirect**

<img width="461" alt="image" src="https://user-images.githubusercontent.com/115549820/214053020-d7c6fb5f-9381-47c7-9a9f-11a41c79a0d8.png">

### Webserver Enumeration

***Dirbuster output***

<img width="478" alt="image" src="https://user-images.githubusercontent.com/115549820/214059152-e4fcc564-4623-4aa9-8c0f-7f1b7a15a6ee.png">

***Nikto output***

<img width="669" alt="image" src="https://user-images.githubusercontent.com/115549820/214054537-59dcaa0f-b80a-47dc-ab23-acaf2c8467e3.png">

***Homepage***

![image](https://user-images.githubusercontent.com/115549820/214591192-f2991a51-e14a-4087-9f02-af2c4512dae6.png)

***Wappalyzer***

![image](https://user-images.githubusercontent.com/115549820/214591349-e2390666-6082-4e6a-b9de-1d342951027a.png)

***Subdomain Enum***

****Wordlist= top1million-5000****

![image](https://user-images.githubusercontent.com/115549820/214599797-5e747c73-90ec-4331-a394-c3f8b6cef8eb.png)

***dev.stocker.htb***

![image](https://user-images.githubusercontent.com/115549820/214600355-53d849cc-55f3-4790-85f4-9aaa77e64352.png)

***Dirbuster: dev.stocker.htb***

![image](https://user-images.githubusercontent.com/115549820/214604804-97048d2a-904f-4610-a944-4cc9cf9f907f.png)

***dev.stocker.htb/login

![image](https://user-images.githubusercontent.com/115549820/214601043-ce1a67cc-0983-44af-8105-f1e2a5782074.png)

***Bypass login***

🔗 https://book.hacktricks.xyz/pentesting-web/nosql-injection#basic-authentication-bypass


![image](https://user-images.githubusercontent.com/115549820/214606203-dc130c36-eb6a-42d6-920e-62584b2e4c46.png)

![image](https://user-images.githubusercontent.com/115549820/214606432-e9aadedc-ce52-41da-a193-e803fae9c5fa.png)

***/stock***

![image](https://user-images.githubusercontent.com/115549820/214610017-9f2d0c90-9564-4057-a951-8abc339ebfb6.png)

***Submit Purchase***

![image](https://user-images.githubusercontent.com/115549820/214610070-669be05b-febe-4e98-9f8d-afccb44c6e6e.png)

![image](https://user-images.githubusercontent.com/115549820/214610143-25860196-c70b-4862-b2f7-696a249167b3.png)

***Exiftool: document.pdf***

![image](https://user-images.githubusercontent.com/115549820/214610312-670c7f03-a7a8-42e6-99ae-b4133df95dd4.png)

***SKIA/PDF***

![image](https://user-images.githubusercontent.com/115549820/214612112-a400a3be-f3ee-458a-9277-8c3e46c1ea6c.png)

🔗 https://book.hacktricks.xyz/pentesting-web/xss-cross-site-scripting/server-side-xss-dynamic-pdf

***Checking burpsuit***

![image](https://user-images.githubusercontent.com/115549820/214613232-05ad3ae2-7a7f-493f-8330-06f852063e3f.png)

![image](https://user-images.githubusercontent.com/115549820/214613592-8e838597-78ae-424d-b143-63e3a965d3e4.png)

![image](https://user-images.githubusercontent.com/115549820/214614542-4c541474-89fe-40e9-a669-65f71c9455f1.png)

![image](https://user-images.githubusercontent.com/115549820/214614593-215acf14-f14e-4a0b-8303-8194350d839e.png)

***Change size of iframe***

![image](https://user-images.githubusercontent.com/115549820/214615627-e24d986a-735d-405a-ae4f-0dc1c80ed78e.png)

![image](https://user-images.githubusercontent.com/115549820/214616083-d93e9f8b-1529-4e88-b520-eacdddb30ec7.png)

![image](https://user-images.githubusercontent.com/115549820/214616144-5070e8c6-f24b-4059-ba1f-9056ada91b6b.png)

> Possible username:\
> angoose

> Database:\
> MongoDB

***Check nginx config***

![image](https://user-images.githubusercontent.com/115549820/214620294-d7442f2e-a1c8-4abc-9370-5f5be58327f2.png)

![image](https://user-images.githubusercontent.com/115549820/214621758-fdbe836b-4790-4203-8630-5c1896d9541d.png)

![image](https://user-images.githubusercontent.com/115549820/214621856-210434a3-7ce5-4d1f-b558-8db4ab87c940.png)

***Check /var/www/dev/index.html /.app /.js/***

> index.html\
> empty

> index.js\
> config file

![image](https://user-images.githubusercontent.com/115549820/214622873-60693f6a-d5eb-4c10-87e4-f938fe8dfec7.png)

> Possible creds\
> angoose::IHeardPassphrasesArePrettySecure


## Fase 2: Getting Access

![image](https://user-images.githubusercontent.com/115549820/214623375-373fb6ab-2473-4c74-86aa-ad8d762c3c24.png)

## Fase 3: Intern Enumeration

![image](https://user-images.githubusercontent.com/115549820/214623649-1a47feea-9f7a-4e98-a307-771956c3e2c3.png)

![image](https://user-images.githubusercontent.com/115549820/214624604-20450f73-7909-4b20-8f8a-30ed0cbb19e6.png)

***Linpeas.sh output***

![image](https://user-images.githubusercontent.com/115549820/214626703-b8dc970f-7fe1-4d60-907a-4d4edacec72c.png)

![image](https://user-images.githubusercontent.com/115549820/214626974-3d5e5f32-2b6b-4fe5-bd6a-3a3f0a8daede.png)

![image](https://user-images.githubusercontent.com/115549820/214627133-0cb54223-cb4a-4cd2-bc28-fd73db8d2c75.png)


## Fase 4: PrivEsc

***sudo -l***

![image](https://user-images.githubusercontent.com/115549820/214625681-b07f01f0-5748-4d7f-85e6-baae0440f76a.png)

![image](https://user-images.githubusercontent.com/115549820/214628244-26590520-1f22-4dfa-bb3a-8f6419b51518.png)

![image](https://user-images.githubusercontent.com/115549820/214630346-0f2165b3-733e-4b31-86c3-dda310d2701f.png)

![image](https://user-images.githubusercontent.com/115549820/214630507-fd924f72-a7eb-4654-8360-d460a61846f9.png)

![image](https://user-images.githubusercontent.com/115549820/214630609-52899ede-5cf4-410f-b197-8b7ba1eaa4ce.png)

![image](https://user-images.githubusercontent.com/115549820/214630729-b78c74f0-c41f-4484-bf1c-21924c418e58.png)

## HackTheBox Questions

> user.txt
> 0ad98e33fd0a74089945fecb2ff3802b

> root.txt
> 914240f0cce596e99224f7772c152a04
