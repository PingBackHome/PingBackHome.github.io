---
layout: post
title: TryHackMe | RootMe
categories: THM
---

## Recon

### Recon\nmap

We start with a simple nmap scan on the IP address: `10.10.99.1`\
The syntax I'm using for the scan is: `nmap -sC -sV -A 10.10.99.1 -o nmap_scan1.txt`\
Explanation:

- **-sC**: This option tells Nmap to scan with default scripts. It runs a set of scripts which are useful for identifying common vulnerabilities and gathering additional information about the target.
- **-sV**: This option enables version detection. It probes open ports to determine service and version information, which can be helpful in identifying potential vulnerabilities.
- **-A**: This option enables aggressive scanning. It combines various options such as version detection, script scanning, and traceroute to provide comprehensive information about the target.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e09232c9-290b-46ba-b927-d180b3144fa7)

As we can see, there are two open ports:\
port 22: SSH\
port 80: HTTP Apache

Let's start with the web server on port 80.

### Recon\port 80

The homepage looks like this:
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/d77fbe34-5c48-4847-94ef-fec7b7072702)

It's always good to take a look at the source code as well, but for now, I don't see anything noteworthy.\
See screenshot:
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/a886d5a9-69bd-42f4-ae22-664acb207894)

Let's use gobuster to see if we can find any directories.\
For this, I'll use the following syntax with gobuster:\
`gobuster dir -u http://10.10.99.1 -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt`

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/334b3e58-2f3c-4174-849a-563f1160a1f1)

From the gobuster output, two interesting directories have emerged:
- /panel
- /uploads

Let's inspect these.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e63b5078-b05d-4faf-92f4-f4e5f0705b02)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/7d5712c2-b591-4729-a481-86c1abe723ac)

It seems that we can upload something at /panel.\
Let's see if we can upload a reverse shell and establish a connection. As usual, we'll use a standard reverse shell from pentestmonkey. \
Let's start with PHP, see link: [php-reverse-shell.php](https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-shell.php)

## Exploit

### Exploit\upload bypass

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/671e9f84-8ceb-4793-a131-39a192937d61)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/0147509d-9f6f-4b1b-9b0a-b66f759fc406)

And we set up a netcat listener on port 5566 on the attacker's machine.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/cb11afcb-849e-4a63-83c2-6954e1b3ed4f)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/ca264d89-87cc-42b8-953b-bfa1de266b6b)

Unfortunately, the server doesn't accept PHP. Let's explore other possibilities.
Let's make several copies of the rvs.php shell but with different extensions.
- .php4
- .php5
- .phtml
We'll see which one works, if any.

The server accepts all three other extensions. See screenshot for success.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/bb5bc18b-ca0c-4cc8-81a2-58af43a608ec)

But how do we trigger these shells? Most likely, we'll see our reverse shell at /uploads.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3138cbbb-5b39-4d82-ba45-143f98c446d8)

And indeed, all three rvs.php* files are at uploads. Let's see which of the three can trigger the reverse shell:

**rvs.php4**
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/951f4d9f-7c28-4932-b719-f8c56a73c160)

**rvs.php5**
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/cb1e7af5-6826-4de8-a166-522b1ceaa80c)

**rvs.phtml**
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/daf6eba5-ee57-474d-aff6-e07779c86bc6)

As you can see above, there are at least two ways to get a working shell on the server.
Now let's go hunting for the two flags.

## Post-Exploit


