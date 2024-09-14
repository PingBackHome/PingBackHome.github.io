---
layout: post
title: TryHackMe | Wonderland
categories: THM/Series/Alice
---





## Recon

### Recon\nmap

**nmap output**

``` golang
nmap -sV -sC 10.10.165.176 -o wonderland_nmap1.txt
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-06-13 08:23 EDT
Nmap scan report for 10.10.165.176
Host is up (0.038s latency).
Not shown: 998 closed tcp ports (conn-refused)
STATE SERVICE VERSION
22/top open ssh OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)

80/tcp open http Golang net/http server (Go-IPFS json-rpc or InfluxDB API)
http-title: Follow the white rabbit.
Service Info: OS: Linux; CPE: cpe:/o:linux: linux_kernel
```


The scan revealed two open ports on the target machine. Port 22 is running an SSH service using OpenSSH on Ubuntu Linux, and port 80 is running an HTTP service with a Golang-based server, possibly related to Go-IPFS or InfluxDB API.\
The HTTP service's title suggests a theme related to "Follow the white rabbit," which may hint at the nature of the CTF challenge.

Because SSH brute force should really be the last resort, we will start with the web services on port 80.


### Recon\http

First, we visit the homepage linked to port 80. See the screenshot below.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/25f9da9a-6d79-4206-8172-ef883e18a804)

When we examine the source code, we also see nothing special, except for some links to directories with images.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/bf9903c2-5469-4e03-bc5b-9599500c293e)
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/ce5414d7-ca77-4621-9d77-08d9b2a7be3f)

**Gobuster**

Okay, the homepage doesn't provide much information. Let's start with a Gobuster scan to enumerate the directories. We will use the wordlist: SecLists/Discovery/Web-Content/raft-small-directories.txt.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/f2d85cfa-2b58-4c29-88d9-48e86947f6fd)

As you can see in the screenshot above, we have added three endpoints:
1. `/img`
2. `/r`
3. `/poem`

Let's view all three endpoints in the web browser.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/8f7e1ef3-54ae-4f93-ab9e-f8f13fd19f82)

As you can see in the screenshot above, `/r` doesn't provide much more than a hint to search further.


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/bda578be-9275-45cc-8975-580db2b0291b)

Just like `/r`, `/poem` is nothing more than a poem, which is of little use to us.


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/a70a30f8-ca4e-4f7b-8e29-e0885a29e3d5)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/d1597388-5ca5-4119-a722-5b3fd19fbfb4)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/a4862725-83f1-4e5d-bd08-f6264a28cee8)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3ea33048-d521-4b63-bcc6-eb2545929472)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e341d114-2cbd-40a0-b841-a43f9ef1bfaf)





















