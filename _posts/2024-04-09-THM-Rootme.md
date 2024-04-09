---
layout: post
title: TryHackMe | RootMe
categories: THM
---

## Recon

### Recon\nmap

We start with a simple nmap scan on the IP address: `10.10.99.1`
The syntax I'm using for the scan is: `nmap -sC -sV -A 10.10.99.1 -o nmap_scan1.txt`
Explanation:

- **-sC**: This option tells Nmap to scan with default scripts. It runs a set of scripts which are useful for identifying common vulnerabilities and gathering additional information about the target.
- **-sV**: This option enables version detection. It probes open ports to determine service and version information, which can be helpful in identifying potential vulnerabilities.
- **-A**: This option enables aggressive scanning. It combines various options such as version detection, script scanning, and traceroute to provide comprehensive information about the target.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e09232c9-290b-46ba-b927-d180b3144fa7)

As we can see, there are two open ports:
port 22: SSH
port 80: HTTP Apache

Let's start with the web server on port 80.

### Recon\port 80

The homepage looks like this:
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/d77fbe34-5c48-4847-94ef-fec7b7072702)

It's always good to take a look at the source code as well, but for now, I don't see anything noteworthy. See screenshot:
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/a886d5a9-69bd-42f4-ae22-664acb207894)

Let's use gobuster to see if we can find any directories.
For this, I'll use the following syntax with gobuster:
`gobuster dir -u http://10.10.99.1 -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt`

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/334b3e58-2f3c-4174-849a-563f1160a1f1)


