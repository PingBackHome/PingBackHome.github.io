---
layout: post
title: TryHackMe | Kenobi
---

# TryHackMe | Kenobi

+++++++++++++++++++++++++++++++++++\
IP:   10.10.160.229\
Date: 18-10-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196421843-23df42b5-ed3a-414b-859f-697f464676dd.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196421964-7abf88d9-08cd-4311-b928-f40d2c1be9f6.png">

**Open Ports**

21     FTP         - ProFTP 1.3.5\
22     SSH         - OpenSSH 7.2p2\
80     Webserver   - Apache 2.4.18\
111    RPCbind     - RPCbind\
139    Samba       - SMBD 3.X 4.X\
445    Samba       - SMBD 4.3.11\
2049   Nfs_acl

### SMB Enumeration

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196426561-f447a269-8902-4be4-a13a-be9a5951349b.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196427161-ae607c30-f072-4f82-a206-a60530da51b5.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196427717-0360e903-36f8-495d-80b5-43997aee1774.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196428845-747ec174-1281-499c-b28c-3a9ba676c164.png">

**Log.txt output**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196428510-00879b9f-1723-41d3-a2cb-a359222eb635.png">



## Fase 2: Getting Access

<img width="786" alt="image" src="https://user-images.githubusercontent.com/115549820/196438315-a83efb0d-3e3c-437f-b16d-77efe76814ef.png">

<img width="583" alt="image" src="https://user-images.githubusercontent.com/115549820/196438888-1af81f69-b1b9-4bbf-be4e-bec03733f71d.png">

<img width="583" alt="image" src="https://user-images.githubusercontent.com/115549820/196439056-5bb3c4de-dcd2-4cba-9d65-957427132311.png">

<img width="694" alt="image" src="https://user-images.githubusercontent.com/115549820/196440376-f4a369c3-3cbb-4f99-ab65-f97bd49acc2d.png">

<img width="694" alt="image" src="https://user-images.githubusercontent.com/115549820/196440604-fc3690a7-9936-4c66-ad67-7c93757c5a21.png">

<img width="444" alt="image" src="https://user-images.githubusercontent.com/115549820/196441422-734b68ff-da2a-4b50-ac20-80dd07802272.png">

<img width="567" alt="image" src="https://user-images.githubusercontent.com/115549820/196441575-3e966a31-8c11-4670-8f3f-b4fc9720f3fd.png">



## Fase 3: PrivEsc

<img width="567" alt="image" src="https://user-images.githubusercontent.com/115549820/196441811-2192cf10-7c35-4e56-b690-b4e7579bcb20.png">

<img width="567" alt="image" src="https://user-images.githubusercontent.com/115549820/196441960-a07e74b8-cdab-48d0-8fc7-4f94efc877e1.png">

<img width="475" alt="image" src="https://user-images.githubusercontent.com/115549820/196442578-6bfb0b15-30b7-4a6d-b6ec-793d6131b119.png">

<img width="475" alt="image" src="https://user-images.githubusercontent.com/115549820/196442819-12eefe20-559a-4361-ba5b-0aa82d648ef3.png">

<img width="475" alt="image" src="https://user-images.githubusercontent.com/115549820/196443065-c2b5a81a-2d8e-4be6-ac2a-7d6ef83dd863.png">


<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196199333-94894948-94ea-436b-9a33-a8e19f5becc2.png">


## TryHackMe Questions

'Scan the machine with nmap, how many ports are open?'
> 7

'Using the nmap command above, how many shares have been found?'
> 3

'Once you're connected, list the files on the share. What is the file can you see?'
> log.txt

'What port is FTP running on?'
> 21

'What mount can we see?'
> /var

'What is the version?'
> 1.3.5

'How many exploits are there for the ProFTPd running?'
> 4

'What is Kenobi's user flag (/home/kenobi/user.txt)?'
> d0b0f3f53b6caa532a83915e19224899

'What file looks particularly out of the ordinary?'
> /usr/bin/menu

'Run the binary, how many options appear?'
> 3

'What is the root flag (/root/root.txt)?'
> 177b3cd8562289f37382721c28381f02
