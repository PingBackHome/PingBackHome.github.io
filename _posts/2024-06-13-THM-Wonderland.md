---
layout: post
title: TryHackMe | Wonderland
categories: THM/Series/Alice
---


```
(kali@kali)-[~/ ... /thm/series/alice/wonderland]
nmap -sV -sC 10.10.165.176 -o wonderland_nmap1.txt
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-06-13 08:23 EDT
Nmap scan report for 10.10.165.176
Host is up (0.038s latency).
Not shown: 998 closed tcp ports (conn-refused)
STATE SERVICE VERSION
22/top open ssh
ssh-hostkey:
2048 8e : ee : fb : 96 : ce : ad : 70 : dd : 05 : a9 : 3b : 0d : b0 : 71 :b8:63 (RSA)
256 7a :92:79:44 :16 : 4f : 20 :43 : 50 : a9 : a8 :47 : e2 : c2 : be:84 (ECDSA)
256 00:0b:80:44:e6:3d:4b:69:47:92:2c:55:14:7e:2a:c9 (ED25519)
Golang net/http server (Go-IPFS json-rpc or InfluxDB API)
I_http-title: Follow the white rabbit.
Service Info: OS: Linux; CPE: cpe:/o:linux: linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 14.40 seconds

PORT

OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)

80/tcp open http
```
