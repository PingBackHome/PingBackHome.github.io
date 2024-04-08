---
layout: post
title: TryHackMe | Mr. Robot CTF
categories: THM
---

_Unraveling MrRobot: CTF_


## Recon

### RECON\nmap scan

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


### RECON\port 80

Now that we have more direction, we can start searching more purposefully. For now, we'll leave the SSH on port 22 aside. Bruteforcing without any credentials can be time-consuming and might not be the right approach. Let's start with the Apache server on port 80. We can do this simply by opening a web browser and browsing to [http://10.10.80.8](http://10.10.80.8), not HTTPS but HTTP (keep this in mind).

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/54f8469d-520b-47ab-9386-f7d5c401dd27)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/1e41dadc-0303-47a6-b8d1-80a4b1fbfb22)

As you can see, we are presented with a window containing various options to choose from. I'll go through them one by one and highlight the interesting/important aspects for you.

Options - Output:

- Prepare = nothing
- Fsociety = nothing
- Inform = nothing
- Question = nothing
- Wakeup = movie clip
- Join = request for your e-mailaddress, hmmm questionable...

Unfortunately, this hasn't yielded much yet. Let's take a look at some source code of the website. Perhaps this will reveal some information that could be useful.

**Main page**
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/87a661b4-9d85-4919-a5d4-9a473787c49d)
The main page reveals little information, let's move on to the next one.

**Join page**
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/66d9ac63-adb2-4f4c-9341-0c28c00edc2e)
Now we have something. If you look at line 8 in the source code, you'll see a reference to `wp-content`, which could indicate that it's a WordPress website. Let's investigate this further.

### RECON\wpscan

On your Kali Linux distribution, the `wpscan` tool is installed by default. With this tool, you can scan WordPress sites for vulnerabilities, plugins, themes, and users. It provides extensive functionality for detecting potential security issues, such as known vulnerabilities in WordPress core, plugins, and themes. Additionally, `wpscan` can gather information about usernames, including admin accounts, and perform brute force attacks to identify weak passwords. It's a powerful tool for assessing the security status of WordPress sites during penetration tests or security audits.

Let's take a look at the syntax of `wpscan`. We can do this by opening the terminal and executing the command `wpscan -h`. Below is the result:
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/b52374b0-48c8-44e5-b8a2-ddbf7cc378e5)

As you can see in the output, we need to provide some parameters with the command. These are `--url` and `-o`, and for now, we'll leave the rest on default settings as we don't have much information yet.

The command looks like this: `wpscan --url http://10.10.148.45 -o wpscan1.txt`.

Let's see what output we get and if it provides us with any useful information.

The output reveals several interesting findings, as shown below:

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e7551594-dea0-41c4-919a-9a8d542cc82d)

We can see that there should be a robots.txt file, and furthermore, XML-RPC is enabled, and the theme being used is identified.

Let's start by examining robots.txt.

### RECON\robots.txt

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/2acf1803-9f10-41fd-a503-b70cac446682)

As you can see in the screenshot above, there are two items we can investigate: `fsocity.dic` and `key-1-of-3.txt`.
If we browse to `key` first, we get the following output:

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/f3668bd5-cc25-4a0d-aa50-45aee1df1270)

Great, we've got the first key!
Now, let's take a look at the second file: `fsocity.dic`.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/c1dad711-aa8d-4ed8-a79b-df608845a67c)

Once we have `fsocity.dic`, I'll first inspect what it contains by displaying the first 15 lines.
I'll do this by executing: `head -n 15 fsocity.dic`, see the result below:

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/1532abd8-fae6-46d4-b6ef-ea55a5902c50)
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/d4035eb9-f4da-4819-ad28-777859cd58fb)

It's always nice to get a wordlist :)
However, it seems quite large to me, so let's play around with it to streamline and shrink it if possible.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/67fb5d87-9cbb-40ad-aa51-46275c8c43a1)
As you may have noticed, the file has become significantly smaller after removing all duplicate entries. We started with approximately 7MB, and currently, we're down to about 95KB :):):)

Okay, we now have a fairly small wordlist. Where can we apply this?\
As you may have noticed, the SSH port is closed, so there must be another way to log in.\
Let's continue with enumeration, let's start with dirb.

### Recon\dirb

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/d0cebb64-8926-4b00-a244-e76dcde98bf7)

As you can see in the screenshot above, there are several things of interest.\
We already know that there is a WordPress site running, so let's take a look at `/wp-login`.
