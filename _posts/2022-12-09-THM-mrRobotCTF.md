---
layout: post
title: TryHackMe | Mr Robot CTF
categories: TryHackMe
---

# TryHackMe | Mr Robot CTF

+++++++++++++++++++++++++++++++++++\
IP: 10.10.106.255\
Date: 09-12-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="338" alt="image" src="https://user-images.githubusercontent.com/115549820/206684025-f04fc705-e411-432b-8578-cb63dc1ec78f.png">

**Open Ports**

22 - SSH - CLOSED\
80 - Webserver - Apache\
443 - Webserver SSL - Apache

### Webserver Enumeration

**Nikto output**

**Dirbuster output: 80**

<img width="476" alt="image" src="https://user-images.githubusercontent.com/115549820/206689137-96afee13-904c-4d42-9633-36739f05a99e.png">


**Dirbuster output: 443**

<img width="478" alt="image" src="https://user-images.githubusercontent.com/115549820/206697300-c572f8ed-5b62-439d-bcab-44f4a2493071.png">

***Homepage***

<img width="1123" alt="image" src="https://user-images.githubusercontent.com/115549820/206686028-a25a3017-6ed4-4139-a84d-fb67f2a77a18.png">

***/Robots.txt***

<img width="318" alt="image" src="https://user-images.githubusercontent.com/115549820/206686181-8edd1e2e-38dc-4a57-8949-eafaf0ea080c.png">

***/fsocity.dic***

<img width="665" alt="image" src="https://user-images.githubusercontent.com/115549820/206686334-f10ba759-82f6-467f-9deb-5e797fb97bd7.png">

<img width="329" alt="image" src="https://user-images.githubusercontent.com/115549820/206686877-35f5e50c-a8db-4a5c-9f7c-d8138961e38e.png">


***/key-1-of-3.txt***

<img width="329" alt="image" src="https://user-images.githubusercontent.com/115549820/206686520-e3477707-d7ad-487c-abf1-9d7cb53b4de2.png">

***source:/inform***

<img width="444" alt="image" src="https://user-images.githubusercontent.com/115549820/206688779-3de36240-1b76-4842-80e5-05501bfc8297.png">

***/0***

<img width="994" alt="image" src="https://user-images.githubusercontent.com/115549820/206697065-e58099f4-f131-49c1-ab2c-924e3fe88f13.png">

***/wp-login***

<img width="681" alt="image" src="https://user-images.githubusercontent.com/115549820/206688910-b0812cda-aeae-4a19-93ed-201e7b7d89a1.png">

**WP-scan**

<img width="478" alt="image" src="https://user-images.githubusercontent.com/115549820/206698778-a72ef257-eaf9-40c0-915a-17f666290a7c.png">

<img width="510" alt="image" src="https://user-images.githubusercontent.com/115549820/206698859-a749c0c0-e3cb-4b79-9511-8071549011f1.png">

***WP username***

<img width="510" alt="image" src="https://user-images.githubusercontent.com/115549820/206699349-135809da-b127-4f6f-9726-fbe2091e0d5c.png">

***WP password cracking***

<img width="510" alt="image" src="https://user-images.githubusercontent.com/115549820/206699850-501da721-679e-4029-9b50-56ae8792f5d4.png">

<img width="834" alt="image" src="https://user-images.githubusercontent.com/115549820/206701642-fe37558e-c848-4985-98d3-8dd2069215bf.png">

<img width="245" alt="image" src="https://user-images.githubusercontent.com/115549820/206701830-1df94de8-ff55-4764-9017-1ef70d6dfc39.png">

<img width="502" alt="image" src="https://user-images.githubusercontent.com/115549820/206701985-1465dde0-aa5e-4d38-8de0-17dd6a080546.png">

<img width="502" alt="image" src="https://user-images.githubusercontent.com/115549820/206711673-20144e69-61d1-43b6-b599-318130556abe.png">


## Fase 2: Getting Access

![image](https://user-images.githubusercontent.com/115549820/207056982-489b0d9c-ef1d-4bda-97e3-cf15b4a4f069.png)

<img width="620" alt="image" src="https://user-images.githubusercontent.com/115549820/207018496-ba18a5a7-478d-49c8-bce2-992bb89196c1.png">

### Reverse shell

![image](https://user-images.githubusercontent.com/115549820/207058314-a7bd3ee6-4c47-4e44-b282-cd4b19e5f1c8.png)

![image](https://user-images.githubusercontent.com/115549820/207058573-d92ed38a-2652-4219-9a61-8768a10c4011.png)

![image](https://user-images.githubusercontent.com/115549820/207058718-b2b73dee-bbee-436a-9012-283ac55f5741.png)

![image](https://user-images.githubusercontent.com/115549820/207058972-2dcdb404-4f86-4b47-948d-c422097bfedb.png)

![image](https://user-images.githubusercontent.com/115549820/207059145-4cb3e795-1452-443b-93b9-aa2432476382.png)

![image](https://user-images.githubusercontent.com/115549820/207060595-338823b3-5bb8-4d11-b593-62627f505016.png)

  
## Fase 3: Intern Enumeration

![image](https://user-images.githubusercontent.com/115549820/207060999-0adeddea-7e15-451c-bdf5-335f1f76d19a.png)

![image](https://user-images.githubusercontent.com/115549820/207061242-41a2ebe4-5dc6-43b2-b815-f9a1162a0357.png)

![image](https://user-images.githubusercontent.com/115549820/207061341-96de46c4-2087-43a9-91e0-465cde0d3515.png)

### Cracking md5 hash

![image](https://user-images.githubusercontent.com/115549820/207063374-6dd25bbe-8ea2-4fce-842c-c829ec9a84bd.png)

![image](https://user-images.githubusercontent.com/115549820/207063484-1c1c7738-8d0c-4259-ad89-35cdbb312b72.png)

![image](https://user-images.githubusercontent.com/115549820/207063658-d587904e-8966-45cf-96f5-50cd216049f8.png)

![image](https://user-images.githubusercontent.com/115549820/207063832-848da3a5-862b-4ba7-9621-c2a0de63c1f1.png)

  
## Fase 4: PrivEsc

![image](https://user-images.githubusercontent.com/115549820/207064484-371951fe-ef31-418e-8b19-eca94afd49e8.png)

![image](https://user-images.githubusercontent.com/115549820/207065736-b15caeeb-3b07-4902-b557-4878c9bfa84d.png)

![image](https://user-images.githubusercontent.com/115549820/207066148-6683d000-9af4-48cc-909a-00264f4af89c.png)

![image](https://user-images.githubusercontent.com/115549820/207066244-9d4e23a9-9aa4-461e-bcb7-4154bad28bb8.png)

![image](https://user-images.githubusercontent.com/115549820/207066739-30ede6ff-6249-4e90-9730-ba1e7a5b9503.png)

![image](https://user-images.githubusercontent.com/115549820/207067025-ac18edab-0d92-45b4-9ec0-2f7018cacf67.png)


## TryHackMe Questions

What is key 1?
> 073403c8a58a1f80d943455fb30724b9

What is key 2?
> 822c73956184f694993bede3eb39f959

What is key 3?
> 04787ddef27c3dee1ee161b21670b4e4
