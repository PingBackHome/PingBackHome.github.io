---
layout: post
title: TryHackMe | Wonderland
categories: THM/Series/Alice
---





## Recon

###Recon\nmap


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
