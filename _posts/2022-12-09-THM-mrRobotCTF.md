# TryHackMe | Mr Robot CTF

+++++++++++++++++++++++++++++++++++\
IP: 10.10.106.255\
Date: 09-12-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="338" alt="image" src="https://user-images.githubusercontent.com/115549820/206684025-f04fc705-e411-432b-8578-cb63dc1ec78f.png">

**Open Ports**

22 - SSH - CLOSED
80 - Webserver - Apache
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


## Fase 2: Getting Access

  
## Fase 3: Intern Enumeration

  
## Fase 4: PrivEsc
  
## TryHackMe Questions

What is key 1?

What is key 2?

What is key 3?
