---
layout: post
title: TryHackMe | Mr. Robot CTF
categories: THM
---

_Unraveling MrRobot: CTF_


## Recon

### RECON\\NMAP scan

As usual, we begin with a simple nmap scan on the provided IP address, in my case, it's IPv4 `10.10.80.8`. I'm using the following parameters in my command:

- `-sV`: This parameter enables version detection, which attempts to determine the version of the services running on the ports discovered during the scan.
- `-sC`: This parameter enables the default script scan. It runs a set of scripts to gather more information about the target, potentially identifying vulnerabilities or misconfigurations.
- `-o`: This parameter specifies the output format for the scan results.

Here's the output I received:

```plaintext
nmap -sV -sC 10.10.80.8 -o scan1.txt
Nmap scan report for 10.10.80.8
Host is up (0.077s latency).
Not shown: 997 filtered tcp ports (no-response)
PORT     STATE    SERVICE    VERSION
22/tcp   closed   ssh
80/tcp   open     http       Apache httpd
|_http-title: Site doesn't have a title (text/html).
|_http-server-header: Apache
443/tcp  open     ssl/http   Apache httpd
|_http-title: Site doesn't have a title (text/html).
|_http-server-header: Apache
| ssl-cert: Subject: commonName=www.example.com
| Not valid before:
| Not valid after:
| 2025-09-13T10:45:03
```

In this output, we can see that ports `22` (SSH), `80` (HTTP), and `443` (HTTPS) are open. Additionally, we have some information about the web server running on ports `80` and `443`, indicating it's Apache HTTP server. The SSL certificate information is also provided for port `443`, showing the common name and validity dates.


### RECON\\Port 80

Now that we have more direction, we can start searching more purposefully. For now, we'll leave the SSH on port 22 aside. Bruteforcing without any credentials can be time-consuming and might not be the right approach. Let's start with the Apache server on port 80. We can do this simply by opening a web browser and browsing to [http://10.10.80.8](http://10.10.80.8), not HTTPS but HTTP (keep this in mind).

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/54f8469d-520b-47ab-9386-f7d5c401dd27)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/1e41dadc-0303-47a6-b8d1-80a4b1fbfb22)

