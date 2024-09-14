---
layout: post
title: TryHackMe | RootMe
categories: THM
---

In this writeup, we'll explore the steps taken to gain access and escalate privileges on a target server.

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

Alright, let's start with where I am, who I am, and what capabilities I have.
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/9fb994d0-4f53-4312-9ed4-0bcbdf39d853)

Hmmm, that didn't give us much information.\
Let's search for the first flag.\
`find / -name user.txt 2>/dev/null`

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/b755c522-b3b4-4a55-a7fd-2814562ebf17)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/45140444-56f7-47c8-8125-1cd23272b804)

We have the first flag :)\
But now we need to be able to read the root.txt flag in the root folder.\
This means we need to gain root privileges, i.e., privilege escalation.

## Privilege Escalation

### Privilege Escalation\suid

We can search for files/programs on the server that are not properly configured and might have root privileges.
We can do this by executing the following command on the server:
`find / -user root -perm /4000 2>/dev/null`

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/a072d7ca-1980-4e6e-9153-82cfe91d883c)

We've received a list of programs that we can inspect via gtfobins. See link:
[gtfobins.github.io](https://gtfobins.github.io)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/82f15366-d2d8-45f8-9ce6-c7f1014cbc82)

I think Python is the best option to exploit root privileges.\
And then I'll scroll to the "File read" section on gtfobins:

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/19df076f-f55b-4c96-88e0-0c752d4d4c28)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/1e97711e-6c15-4546-8151-34638e833be5)

We now have both flags :)


# Summary 
1. **Initial Scan:**
   - Conducted an initial nmap scan on the IP address `10.10.99.1` using the command `nmap -sC -sV -A 10.10.99.1`.
   - Identified two open ports:
     - Port 22: SSH
     - Port 80: HTTP Apache

2. **Web Server Exploration:**
   - Explored the web server on port 80.
   - Found nothing significant on the homepage.
   - Inspected the source code but found no noteworthy information.

3. **Directory Enumeration:**
   - Utilized gobuster to search for directories.
   - Discovered two interesting directories: `/panel` and `/uploads`.

4. **Reverse Shell Attempt:**
   - Attempted to upload a reverse shell at `/panel` but found out the server didn't accept PHP.
   - Tried different file extensions (`php4`, `php5`, `.phtml`) for the reverse shell and found that all three were accepted by the server.
   - Located all three reverse shell files in the `/uploads` directory.
   - Tried triggering the reverse shells to establish a connection.

5. **Flag Retrieval:**
   - Successfully found the first flag by searching for `user.txt`.

6. **Privilege Escalation:**
   - Explored potential privilege escalation by searching for files/programs owned by root and with the setuid bit set using the command `find / -user root -perm /4000 2>/dev/null`.
   - Received a list of programs to inspect via gtfobins.
   - Determined Python as the best option for exploiting root privileges and scrolled to the "File read" section on gtfobins.

7. **Flag Acquisition:**
   - Successfully obtained both flags.


