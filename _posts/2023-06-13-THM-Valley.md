---
layout: post
title: TryHackMe | Valley
categories: THM
---

# TryHackMe | Valley
+++++++++++++++++++++++++++++++++++\
IP: 10.10.234.244\
Date: 13-06-2023\
+++++++++++++++++++++++++++++++++++

## Recon

**Nmap scanning**

Nmap Scan Results for IP Address 10.10.234.244

<img width="598" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/a1ba5e68-71d0-4c66-b6e2-1353b6d28866">

**Open Ports**

The scan revealed the following open ports:

1. Port 22/tcp (SSH): This port is open and running OpenSSH 8.2p1 on Ubuntu Linux. It supports secure remote shell access.

2. Port 80/tcp (HTTP): This port is open and running Apache httpd 2.4.41 on Ubuntu. It serves HTTP web content.

**Conclusion**

Based on the Nmap scan results, the system at IP address 10.10.234.244 has SSH (port 22/tcp) and HTTP (port 80/tcp) services running. The SSH service allows secure remote shell access, while the HTTP service serves web content.

**Dirbuster scanning**

Homepage(screenshot)\
<img width="951" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/ed110a3e-5cd9-4859-bb6b-7021a4f4f573">

Output dirbuster scan\
<img width="889" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/5779f84c-d2c7-45b5-ae4d-63d72f62790b">

note.txt\
<img width="551" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/53a8662a-23a5-4add-ac68-06f7de1d58f6">

Further Investigation Options

After obtaining limited information, we have several options to proceed:

1. We can conduct a more comprehensive Nmap scan using the `-p-` flag to scan all ports.
2. Fuzzing subdirectories.
3. Password spraying on the SSH port.

Let's start with the first two options. I will initiate an Nmap scan with the additional `-p-` flag, and simultaneously start the Dirbuster scan on `<ip>/gallery`, `<ip>/static`, and `<ip>/pricing`.

Nmap Scan with All Ports

To conduct a thorough scan of all ports, use the following Nmap command:

`sudo nmap -sC -sV -A -p- 10.10.234.244 -oN valley_all_nmap.txt`

**Results nmap scan**

<img width="672" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/0ffeab58-da45-49eb-85ec-61bed8aff8c5">

As you can see, the results between the two nmap scans are different. \
In the last nmap scan, an FTP service (vsftpd 3.0.3) was found on port 37370. \
We will set this finding aside for now and first see what comes out of the dirbuster scan.

**Dirbuster output**

/gallery : nothing\
/pricing : nothing\
/static : something :)

<img width="672" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/60385984-063e-42d0-bb58-421749a5208e">

/static/00:\
<img width="459" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/1b7a5010-b942-461e-b87a-9c4525946d9b">

As you can see in the screenshot above, there is a note left by valleyDev, and item 3 on the list looks interesting. \
Let's visit it: `/dev1243224123123`.

<img width="1101" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/85c0b23f-3e06-490e-9261-ffcb1e218206">

The credentials `admin::admin` do not work. \
Let's first read the source code to understand which function the login screen uses to verify passwords/usernames.\
<img width="575" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/61b9ab36-6b17-45a9-af2c-bdcf872c6401">

If we examine the source code, we can see on line 9 that a `dev.js` script is being used. \
Let's investigate further.

<img width="634" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/895552f6-c58d-4d47-8398-48d7d47b8966">

As you can see in the screenshot above, the username and password are in clear text in the source code: `siemDev::california`. \
Below that, we see a redirect to `/dev1243224123123/devNotes37370.txt`.\
Let's try logging in with the given credentials and see where we end up.

<img width="550" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e68d780e-77c8-4f02-a3f7-5b688a106339">

We end up on another page with a note, and item 1 is very interesting. \
We have already encountered item 4: FTP on a strange port during the second nmap scan.\
Let's see if we can log in to the FTP and/or SSH using the credentials we have.

**FTP enumaration**

On the FTP server, there are multiple files:
siemFTP.pcapng
siemHTTP1.pcapng
siemHTTP2.pcapng

Let's transfer all of them to our Kali machine using the command `get <filename>`.\
Once they are downloaded, we can further investigate them.

<img width="966" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/ec82e9ad-cc55-43f4-91dd-56ba37e49d64">

Just to be sure, I will check if there are any known exploits for the vsftpd service using `searchsploit`.\
In the screenshot, you can see that there is only a `denial of service` exploit available, which is not useful for us.

<img width="966" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/56e0bc22-e62d-4c8e-85b4-aa9d6a9003f6">


**FTP files**

We will first examine the pcap file of the FTP traffic by loading it into Wireshark. Wireshark is a default tool in Kali Linux, so let's start it.\
There are a few queries that I want to run on the pcap. First, I want to check if there have been any other logins used besides the ones we already know. \
We can do this by executing the following query:\
`ftp.request.command == USER || ftp.request.command == PASS`

Explanation:
To analyze the FTP traffic in the pcap file using Wireshark, we execute a query to filter the FTP requests. 
The query `ftp.request.command == USER || ftp.request.command == PASS` filters the packets that contain either the FTP command USER or PASS, which are typically used for username and password authentication during FTP login attempts. \
This query will help us identify any additional login attempts made on the FTP server beyond the credentials we already have.\

<img width="966" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/d367239e-1057-4857-89e5-cffb1798a441">

Furthermore, we will check if any files were downloaded or uploaded to the FTP server that could be of interest.\
The query to check for downloads is:\
`ftp.request.command == RETR`\
The query to check for uploads is:\
`ftp.request.command == STOR`

The previous queries (ftp.request.command == RETR and ftp.request.command == STOR) did not provide the expected results, indicating that there were no notable file downloads or uploads via FTP. Therefore, we will shift our focus to analyzing the pcap files that contain HTTP traffic.

After analyzing the FTP traffic without significant findings, we will now shift our attention to the second pcap file, siemHTTP1.pcapng, which captures HTTP traffic.

To identify potential login attempts in plain text, we will execute the query `http.request.method == POST`. 
This query filters the HTTP traffic and retrieves packets where the request method is POST, which is commonly used for submitting login credentials.

Unfortunately, this query does not yield any results, and there is little to find in this file. \
I have also checked for unusual redirects using the following query:\
`http.request.method == POST && http.request.uri.path contains "login"`

However, nothing relevant was found based on this query.

Now, let's proceed to the last file and hope to find some valuable information. 
I will repeat the queries from the previous pcap.

Finally, we have a result using the query `http.request.method == POST`!\
<img width="966" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3ecfc669-b654-4531-a700-43dd953d7096">


As you can see in the screenshot, we have found credentials in plain text: `valleyDev::ph0t0s1234`.\
Now we have only one place left to try these credentials, let's see if they work for the SSH service offered on port 22.


## Acces

<img width="610" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/cb163346-8a8d-4fb6-9f5c-c94f8f1bd0cd">

Having successfully logged into the machine running Ubuntu 20.4.6, it's time to perform enumeration. \
This process involves gathering information about the system, such as installed software, network configuration, user accounts, and other relevant details, to gain a better understanding of the system's environment.

Before proceeding with enumeration, it's important to retrieve the contents of the user.txt file, which likely contains the first flag or important information needed to progress further.\

`user.txt::THM{k@l1_1n_th3_v@lley}`

**valleyAuthenticator**
After exploring the contents of valleyDev's home directory without finding any further relevant information, we decide to navigate up one level in the directory structure. During this process, we discover an executable file that catches our attention due to its peculiar nature.

<img width="610" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/40d351fb-31e8-4098-8485-e371fbdb6f94">

The user wants to determine the file type of the executable file. To do so, the file command is used, which provides information about the file's type and characteristics. \
The output of the file command will reveal the nature of the file.\
<img width="610" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e6ef4a05-8502-4d85-a9a9-9e07905afd4c">

If we see that it is an executable file, let's proceed with running it.\
<img width="610" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3721466f-0ad5-44c9-bd43-790d2f0bf5d4">

If executing the file didn't provide any meaningful results, let's check if the `strings` utility is installed on the machine by executing `whereis strings`.\
<img width="610" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/cbf0e3f1-bef7-49b0-893f-5312b1791530">

As you can see, the `strings` utility is not installed on the victim's machine. To proceed, let's copy `valleyAuthenticator` to our local machine using the `scp` command.\
`scp <username>@<IP>:/home/valleyAuthenticator .`

<img width="610" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/c1d5431e-0555-47e3-9e2d-f25f0c6d9e05">

<img width="610" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/82f3760c-4e48-4a88-88d6-2e15cd02c5bb">

<img width="610" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/de81c935-3bcc-4ea0-b797-f61600093f79">

Now that we finally have the `valleyAuthenticator` file, we can examine its contents using the `cat` command. 
However, since it might result in excessive scrolling, let's open the file with `nano` for easier navigation and readability.

<img width="610" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/52920336-e703-4a57-a0d3-b56e8e204dbb">

As you can see in the screenshot, there is an interesting hash found on line 6448: `e6722920bab2326f8217e4`.
When we run this hash through CrackStation, we discover that the hash was already known.

<img width="1081" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/6529e674-f362-4a57-b329-09f361c187e0">

valley::liberty123

<img width="312" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/b0d5e454-909f-4dfd-b992-8895c5453778">

## PrivEsc


**Cronjob**

Since the user "valley" still cannot execute `sudo -l`, let's check the cron jobs. \
You can find cron jobs in the file `/etc/crontab`.

<img width="684" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/ab8f9b08-ed42-4449-a13a-8806b47ab4fd">

As indicated in the screenshot, there is a cron job running a .py file called `photosEncrypt.py`. Additionally, we observe that the script is executed using `python3`, which is useful information to remember.
Let's examine the contents of this script to understand its functionality.

<img width="681" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/742ab94c-21da-4be0-8ec9-746f7dffebab">

We can see that the script invokes the `base64` library. Let's explore if we can leverage anything from it, such as checking for write permissions or other possibilities.
But first, we need to locate the library on the machine.

<img width="681" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/2f8be249-56c6-4c1b-be6e-16a00445d205">

The group owner of `base64.py` is `valleyAdmin`, and luckily, I happen to be a member of the `valleyAdmin` group as well. \
This means we have write permissions on `base64.py`. \
Let's take advantage of this opportunity by suggesting to insert a Python 3 reverse shell into `base64.py`.\
You can find a Python 3 reverse shell at: https://www.revshells.com/.

<img width="1155" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/096b7564-21ba-4b9f-a2ea-6c93cee4314c">

Now that we have the code for the reverse shell, we need to place it in `base64.py`. \
If you want to use the reverse shell code, you need to make some modifications.\
For example, remove the reference to `python` and place the import statement for the required libraries below the existing import statements.\
Once you have made the necessary changes, you can set up a netcat listener. I will be using the following flags with `nc`: -nlvp.

<img width="653" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/1ed9db5e-4cdb-4169-aa53-aa00af40c81c">

<img width="653" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/f42d219d-6db3-4d69-92c3-0bc82f42af33">

Great! Now that you have a root shell, we can proceed and search for the final flag, `root.txt`. Let's read it using the `cat` command:

`cat /root/root.txt`

<img width="653" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/fab4a282-7714-46d8-99d2-6610df87240e">



**Summary of CTF Valley Questions:**

This summary provides an overview of the steps taken during the Valley CTF to accomplish user and root flag objectives.

**Summary of CTF Valley Questions:**

1. Discovered SSH service on port 22 and an HTTP service (Apache) on port 80 during the initial Nmap scan.
2. Found interesting note from valleyDev.
3. Explored /dev1243224123123 location on the website.
4. Inspected source code to understand login verification process.
5. Investigated dev.js script mentioned in the source code.
6. Uncovered plain text usernames and passwords in the source code.
7. Attempted login with obtained credentials on FTP and SSH services.
8. Successfully logged in to FTP using siemDev::california.
9. Retrieved multiple files from the FTP server.
10. Checked for known exploits related to vsftpd service.
11. Analyzed PCAP files for FTP traffic, but no new credentials or interesting transfers found.
12. Examined PCAP files for HTTP traffic and discovered new credentials: valleyDev::ph0t0s1234.
13. Logged in successfully to SSH using the new credentials.
14. Obtained user flag on the Ubuntu 20.4.6 system.
15. Discovered an executable file named photosEncrypt.py.
16. Explored the content of photosEncrypt.py and identified the use of


