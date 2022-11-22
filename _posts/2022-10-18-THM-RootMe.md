---
layout: post
title: TryHackMe | RootMe
---

# TryHackMe | RootMe

+++++++++++++++++++++++++++++++++++\
IP: 10.10.196.187\
Date: 18-10-2022\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196382283-9c04a341-80b8-435f-b1f5-8f91b165ec48.png">

**Open Ports**

22    SSH        -   OpenSSH 7.6p1\
80    Webserver  -   Apache 2.4.29

### Webiste Enumeration

**Nikto Scan**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196385654-6b2b257c-98ae-4357-9692-a0490ae2300c.png">

**Homepage**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196384481-02dc98c3-2993-4ec9-8ba6-3a6d469800a3.png">

**Dirbuster Scan**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196386393-ffceed6e-96ce-4b22-a8f0-2a2e93bd1465.png">

## Fase 2: Getting Access

**Uploading Reverse Shell**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196386752-b68832e3-dc4c-411c-83be-36342fda727b.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196387474-cf9846fa-49f2-4e2f-8167-796f86fa31ed.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196387684-5c712295-ae01-4fe0-8fb9-6631859ee70c.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196388339-e8a41656-2ad1-4c40-b235-a9372eaa1897.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196388214-1d335ff9-4353-4f13-88d9-52ca97a08931.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196388570-ae0b370c-3fde-47a0-a1f9-2fac60202439.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196389961-8452f1b6-59b2-4b0c-98a5-2ea1fc19e1e0.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196389850-ba95e477-7a35-4cf5-b5fb-57d0824fb4f9.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196391246-73d532dd-7795-4a8b-8f3c-1c50e9f37c2c.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196393013-b15950d3-9e06-4b79-97c3-76f5accec7d7.png">


## Fase 3: Intern Enumeration

**Upgrade Shell**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196394395-d4719317-135d-4700-a810-8918a0bd3a0c.png">

**Uploading Linpeas.sh**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196395372-5aa0cc5a-367f-4c1f-a194-f1e25f0efc38.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196395516-0b3bcf9b-3264-4380-9402-299151745b05.png">

**Results Linpeas.sh**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196396481-0601fc3f-4265-4fee-b69d-8af337e09b56.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196396769-5562350a-4b7d-4ab3-9ae6-3aae026ffae2.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196399908-4ec92136-a3ab-4827-bb45-33a8cbc4d7a2.png">

## Fase 4: PrivEsc

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/196401870-507be5e1-d4fd-4aac-b294-2f0b0e54e472.png">

## TryHackMe Questions

'Scan the machine, how many ports are open?'
> 2

'What version of Apache is running?'
> 2.4.29

'What service is running on port 22?'
> SSH

'What is the hidden directory?'
> /panel/

'user.txt?'
> THM{y0u_g0t_a_sh3ll}

'Search for files with SUID permission, which file is weird?'
> /usr/bin/python

'root.txt?'
> THM{pr1v1l3g3_3sc4l4t10n}
