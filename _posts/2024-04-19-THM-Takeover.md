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

Let's also start a `gobuster` scan with flags `dir` and `vhost`.\
For the `dir` flag, I'll use the standard directory wordlist `dirbuster/directory-list-2.3-medium.txt`, and for `vhost`, I'll use `amass/subdomains-top1mil-110000.txt`.


