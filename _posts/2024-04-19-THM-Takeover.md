---
layout: post
title: TryHackMe | TakeOver
categories: THM
---



As the hint for this task suggests, it is important to modify our hosts file by adding the IP address and hostname of the box to it.


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/b3c0e69d-3d6e-4798-9cf3-6470983bf7ea)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e40ba9d1-62b0-4b8e-88ba-ddd0aebaab50)


##Recon

### Recon\nmap

Now that we have done this, we will proceed with our customary nmap scan over the box.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/20e9ac60-2b24-4bf9-b6b8-2c166dd01d6a)


We have multiple ports open: port 22 for SSH, port 80 for Apache HTTP, and port 443 for Apache HTTPS.

Let's start by examining what is present on the webserver.

**https://futurevera.thm**

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/628e9a03-f45e-49cb-b251-fbf8db0fb0ff)
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/97ebdc9b-e86b-4119-a55c-b561ae527084)

### Recon\gobuster

Let's also start a `gobuster` scan with flags `dir`, `vhost`, and a vhost with the flag `-k` for HTTPS.\
For the `dir` flag, I'll use the standard directory wordlist `dirbuster/directory-list-2.3-medium.txt`, and for `vhost`, `/usr/share/wordlists/dirb/big.txt`.

**dir\output**

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/7916b428-9f8e-497c-bb20-9e62488b39c2)

**vhost\output**

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/f33a0829-d6ad-42c7-92f6-e1abc9dfe23d)

**vhost_ssl\output**

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/991c135f-7109-477d-9649-838428ce0f67)

Okay, we have found several items:
- suport.futurevera.thm
- blog.futurevera.thm
- portal.futurevera.thm
- payroll.futurevera.thm

Let's add these subdomains to the hosts file and see if we can find anything interesting.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/66010fb4-a499-45ac-9f5e-f0478897bd81)


### Recon\subdomains

**blog.futurevera.thm**

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/531d8b50-5cb2-4349-bd08-44fbce5e8b56)
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/fc5cf002-adac-4532-929a-92095a4c6d97)
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/46816664-71c0-4bc9-86ba-4fbdced12985)

**payroll.futurevera.thm**

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/4c29aba7-b9d0-4349-a4fc-9436ea624409)

**portal.futurevera.thm**

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/ac2a5a63-5519-4d39-bc87-d4245427e01a)

**support.futurevera.thm**

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/fc575dfb-3cc8-4a00-9d0a-4188a07455bd)
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/fb740e66-da4a-4dee-99ca-e55ab939b123)














