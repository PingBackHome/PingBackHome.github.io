---
layout: post
title: TryHackMe | Opacity
categories: THM
---


We are doing a CTF called `Opacity` today. As always, we start with an nmap scan of the IP address we received from TryHackMe.


## RECON

### RECON\nmap

For the nmap scan, I'm using the following parameters:
- `-sV`: This performs a version detection scan, where Nmap tries to determine the version of services on the scanned ports.
- `-sC`: This performs a script scan using the default scripts built into Nmap.
- `-o`: This specifies that you want to save the output to a file. You need to provide a filename, for example, `-o output.txt`.

Let's now run the nmap scan with these parameters and see what we discover! 😊

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/38faf858-aac0-427a-9a55-4152ac580292)

From the output, we see that we have multiple entries on the box:
- Port 22: SSH
- Port 80: Apache webserver
- Port 139: SAMBA
- Port 445: SAMBA

Let's begin web server enumeration.

### RECON\webserver

When we visit the web page in the browser, we arrive at a login page.\
Before attempting to brute force the login page, let's start a `gobuster` scan.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/9f8ed00a-d341-4bbf-a9c4-080a9499b010)

Since the login form web page displayed a `.php` extension, I'll specify to `gobuster` that it should include that extension in the scan.
Additionally, I'll use the `common` wordlist for this scan.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/502a8cb4-67a7-48bc-8715-e638da26b5ea)

The `common` wordlist doesn't yield much, so let's use the `big` wordlist for the next scan.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/75a1c602-d8f1-4da8-8c08-3972e75aff13)

The `big` wordlist gives us 1 additional endpoint, `cloud`.
Let's start another `gobuster` scan from this endpoint; perhaps it will yield something interesting again

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/c3d5538f-5a52-4d57-aff0-7d9ba65fc0f6)

As you can see in the screenshot above, we have received two new endpoint: /cloud/images and /storage.php.

## EXPLOIT

### EXPLOIT\shell_upload

If we browse to <IP>/cloud in our browser, we arrive at a page where we can upload an image and visit it with the provided link.\
We already know that the backend accepts PHP, so the next logical step is to upload a PHP reverse shell.


A regular .php shell is not accepted by the backend, so we need to append an extension that is accepted by the page. \
As you can see below, the .php.jpg extension is not accepted.


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/7ce88dac-62e2-4a09-bd60-fd1825adad03)

Let's try another extension, I'm using `shell.php#00.jpg` for this attempt.


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/d1aeb4f0-a30e-4013-afe0-e1731e831f95)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/bc2d4d37-2d7d-4a86-a8cf-b559c05ef7b3)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/8d3d1f7f-9ec9-4df8-b6dd-2257f98fccc4)


As you can see, we have an active callback in our reverse shell. We're in :) Let's go hunt for the first flag of this box.

## PrivEsc

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/143f8222-a2e4-4cdb-bcf2-ff123a9e642b)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/38dbd4a1-0b71-4eb5-8093-cbc101b8cc28)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/147634cb-c00b-4394-ac0b-469db5a231a1)

As you may have noticed, we have limited capabilities as this user. We can't read the first flag (local.txt) as the current user.\
However, we do find something interesting in the /opt folder of this machine.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/9889787d-d900-4a7b-b24d-1db0e558ac19)

If we use the `file` command on the object `dataset.kdbx`, we see that it's a `Keepass` database. This could be very interesting; let's transfer this db to our local machine.\
The easiest way to transfer this file to our local machine is by starting a simple Python server and using `wget` to transfer the file. Let's do this.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/912cef37-1808-4019-98bf-a494789905fb)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e6a4fdc5-6856-46b2-b19f-4e0f77c8f047)

We now have dataset.kdbx on our local machine, but now we need to do something with it. Let's consult `HackTricks` for more assistance.


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/344b6f1b-0812-4d77-890e-856163891a9c)

Let's first install `Keepass` on our machine.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3c61352f-e694-40c1-a7ff-3f095e9a8221)



![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/bac07445-c25f-4077-b37c-660095ea9124)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3df86df0-26f3-4e93-be45-cfb87ced2389)

If we follow the instructions from `HackTricks` and crack the hash with `john` using the standard wordlist `rockyou`, we get a cracked password.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/7468d519-a9cb-48f2-89d5-0d2009ac4c0d)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/ffdfac4b-ed7f-4326-9dce-e03ce22dc3ce)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/d944b17f-d18a-441a-833b-3d0614f5c1cb)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/84de3cab-7b1c-4c65-b012-bb0af4a0fd7d)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3c7589e1-1af4-4a36-a864-139a8d0fd508)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/2036f795-1e17-42af-b996-313ade019c10)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/2c64058a-c90e-46d1-82fa-66bcac6d2d71)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/38adf574-0912-4119-a365-fe4dab004c86)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/608bead5-e4a2-4723-99e1-1a3ba037b0aa)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/2f1690a0-d742-4bff-b893-559522a4d53f)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/6c05c5c5-217e-4c1b-9b82-a21a9f73fe43)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/b0d5a67e-76cf-414b-99cb-e73dc80a7cfd)

