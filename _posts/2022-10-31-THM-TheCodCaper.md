---
layout: post
title: TryHackMe | The Cod Caper
---


# TryHackMe | The Cod Caper

+++++++++++++++++++++++++++++++++++\
IP: 10.10.43.111\
Date: 31-10-2022\
+++++++++++++++++++++++++++++++++++

## Task 2 - Host Enumeration

'How many ports are open on the target machine?'\
<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/198971590-7790a9b6-4527-4b37-a1c7-6517b6942d70.png">
> 2 open ports

'What is the http-title of the web server?'\
<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/198972025-1e1c6995-80cb-4315-9c98-1ac87debb938.png">
> Apache2 Ubuntu Default Page: It works

'What version is the ssh service?'\
<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/198972264-e4d8a77e-e711-4bc9-b3ec-3ebf219568f8.png">
> OpenSSH 7.2p2 Ubuntu 4ubuntu2.8

'What is the version of the web server?'\
<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/198972583-a194ccb8-3250-4794-ac41-b2111a1c6c39.png">
> Apache/2.4.18

## Task 3 - Web Enumeration

'What is the name of the important file on the server?'\
<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/198976446-56eed059-1e61-4ef1-b145-5ed6a5e78ad5.png">
> adminitsrator.php

## Task 4 - Web Exploitation

<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/199005214-8b243cd4-d302-4c04-abe6-2c2341a02173.png">

'What is the username?'\
<img width="93" alt="image" src="https://user-images.githubusercontent.com/115549820/199005293-5306cc37-074d-4e2c-bdf5-8abe0f6d11cf.png">
> pingudad

'What is the admin password?'\
<img width="93" alt="image" src="https://user-images.githubusercontent.com/115549820/199005352-183aa762-634d-42aa-8e27-b0a8914a0b3f.png">
> secretpass

'How many forms of SQLi is the form vulnerable to?'\
> 3

## Task 5 - Command Execution

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199006807-e945faa2-3152-4e93-9099-897a30e6e6cc.png">

<img width="250" alt="image" src="https://user-images.githubusercontent.com/115549820/199006903-02df3001-73a5-4b5f-b501-57082d9aa2d0.png">

<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/199006948-61e38c12-5c89-4650-88b4-1396207bb87f.png">

<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/199007201-b143013a-fe8f-47a1-b6f6-bfbe3ccb2213.png">

'How many files are in the current directory?'\
<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/199007255-381dfc93-0f01-4ce7-abf6-a5378d27372f.png">
> 3

'Do I still have an account?'\
<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/199007484-ca91fab0-7ea9-4142-ba1e-8de08bd2253a.png">
> Yes

'What is my ssh password?'\
<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199007876-5baf9e98-b2bb-41fd-98b2-6a4877542c7a.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199010088-16d13f0b-8f28-44fe-b562-23c11fc7b7df.png">

<img width="535" alt="image" src="https://user-images.githubusercontent.com/115549820/199010331-b6f81e25-fe30-4fc5-8126-ca4e1e8469b1.png">
> pinguapingu

## Task 6 - LinEnum

'Whats is the interesting path of the interesting suid file'\
<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/199013048-aa8fc0d8-0f7d-4152-a56f-8fca60d0b794.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199013203-14d72cc8-d99c-472e-8cba-3249c589655c.png">

<img width="700" alt="image" src="https://user-images.githubusercontent.com/115549820/199014567-ec1e9c34-d10d-437a-b4cc-4c618fae2c9a.png">
> /opt/secret/root

## Task 7 - pwndbg

'Read the above'
> Done

## Task 8 - Binary-Exploitation: Manually

'Woohoo!'
> Done

## Task 9 - Binary-Exploitation: Auto

'Even more woohoo!'
> Done

## Task 10 - Finishing the job

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/199018767-cd9be70f-267a-4e07-b184-1164be9c1118.png">

<img width="874" alt="image" src="https://user-images.githubusercontent.com/115549820/199019642-869baf37-ddea-4eb7-9dcc-bb18e4796569.png">

'What is the root password?'
> love2fish
