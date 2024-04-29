---
layout: post
title: TryHackMe | Agent T
categories: THM
---


_Join me on an exhilarating journey through the Agent T challenge on TryHackMe, where we navigate the depths of cybersecurity, uncovering vulnerabilities, and mastering the art of exploitation to seize control_


## RECON

### RECON\nmap

As usual, we start with an Nmap scan of the machine.\
We use the default parameters for this scan:\
-sV: Service version detection\
-sC: Script scanning

Below is a screenshot of the output:

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/fd562409-c1d0-4c11-9777-795e3c45feba)

We have identified 1 open port, hosting a web server on port 80.

### RECON\webserver

Upon visiting the page in the browser, we encounter a demo admin panel where functionality seems limited. Links appear to be inactive.\
Let's launch gobuster scans targeting both `dir` and `vhost` to further explore the web server.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/7ebbf4a2-9485-45cc-bf3a-40e983f2e2df)

Our gobuster search returns an error that I can't quite place. Let's resort to another standard tool in Kali Linux.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/ed24ba62-06fa-4c32-8bca-b09ea37b6359)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/1a5e8f22-3dd8-4198-a68a-b13168cc5e24)

The Dirbuster output also does not reveal any interesting findings. Perhaps `wfuzz` will yield the desired results.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/daf1950d-c9f9-48f7-a8d6-dd11d271e3b0)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/16956600-e4f2-4c24-a66c-ac7c6cfdee6a)

Unfortunately, the website enumeration has not been successful thus far.

## EXPLOIT

### EXPLOIT\php

From the output of the Nmap scan, it appears that the server is running PHP 8.0.1-dev.\
Running this through `searchsploit` yields the following hit:

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/23687ad0-0584-4049-8746-0dff2c632d4c)

Let's copy the exploit to our working directory and examine how it works.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/05d3da2d-866e-43e5-b908-aaf4f20d4b53)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/61f6db95-fd05-499a-8ba6-664732d0ab21)

Upon reviewing the exploit, as shown in the screenshot above, we notice that the script prompts for user input upon execution.\
No further input is required.
We execute the exploit and provide the requested information. In my case, this is: http://10.10.80.215

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/1082e592-8ea1-4a2d-99dc-9b9dbb3fcfaf)

As depicted in the screenshot above, we have successfully obtained a shell.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/1c6b79ef-0f1a-484a-b9e7-5f1106f88d09)

Now that we have escalated privileges to root, we can proceed to locate the root flag.

Due to the inability to change directories, we resort to using the `find` command to search for the flag.


















