---
layout: post
title: TryHackMe | Mr. Robot CTF
categories: THM
---

# Unraveling MrRobot: CTF


## Recon

### NMAP scan

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
