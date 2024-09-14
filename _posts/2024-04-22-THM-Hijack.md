---
layout: post
title: TryHackMe | Hijack
categories: THM
---


_Exploring a vulnerable machine's security, we uncover weaknesses, escalate privileges, and secure two elusive flags._


## Recon

### Recon\nmap

I initiated an Nmap scan on the TryHackMe box using the following parameters:

- `-sV`: Service version detection
- `-sC`: Script scanning

Here's the output from the scan:

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/403762ed-b5a5-4f84-a947-ecc47ce371b4)

The scan reveals that there are 5 open ports:

- **21:** vsftpd 3.0.3
- **22:** SSH
- **80:** Apache 2.4.18
- **111:** rpcbind
- **2049:** NFS share

### Recon\ftp_1

Now, let's check if we can log in to the FTP server with default credentials.\
anonymous::anonymous

Searchsploit doesn't yield any exploit for this version of vsftpd.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/cf93923f-f9ec-4eca-b181-21f9895590aa)

Attempting to log in with the default credentials on the FTP server proved unsuccessful. We'll set this aside for now and focus on exploring the next open port.

### RECON\webserver

Let's visit the page through the browser and see if we can find an entry point.

At the top of the navigation bar, we see several pages we can visit:

- Administration
- Login
- Sign up

We'll explore each page individually.

**index.php**

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/4e594c4a-62a9-4e53-ad96-723ee92b2c5b)

**administration.php**

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/cb0e5a4d-bb85-46f0-9651-b800bc4f1d67)

We can only view the `administration.php` page if we are admin, which could be interesting if we have admin logins.\
Let's continue exploring.

**login.php**

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/6a28660c-441d-411a-a9a0-3e34050c42c9)
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/b17a2ab5-3e6a-4329-b2f2-a5253c583053)

When attempting to grab low-hanging fruit, such as entering `admin::admin` on the `login.php` page, we notice that we receive a different error message compared to when we provide incorrect `username::password`.

**signup.php**

We create a test account with the following credentials: `hjack::hijack`. 

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/56b69489-c009-44ec-98b4-07bac13c1ae6)
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/411b1c34-cc73-49f1-a953-3c76be182c7a)
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/909925e0-9ba7-4e46-8c46-4a689fbd1afd)

However, upon logging in with these credentials, we find that we still have limited access.


**gobuster**

As a precaution, I initiate a Gobuster scan with standard parameters and the common wordlist.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/99fc812b-98c1-47c9-b83b-002d9cdc72bc)


Unfortunately, the Gobuster scan doesn't yield much more. However, we do spot `config.php`, which could be a place to look later if we gain access to the server.

### Recon\nfs

### NFS Share Discovery

The Nmap scan reveals the presence of an NFS share.\
Let's identify the name of the share so we can mount it to our local machine.
### Identifying NFS Share Name

To identify the name of the NFS share, I utilize the standard Linux tool `showmount` with the `-e` flag, which prints the list of exported directories.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/8ea87c2e-b7c5-45a2-8c59-8e257ae366b5)

From the output, it appears that the share is named `share`. Let's proceed to mount it to our local machine.

First, I create a directory named `nfs_hijack` on my machine, to which I will mount the NFS share.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/ba4e0de1-365e-41cb-980e-36ed7fc7d91b)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/fad63e1c-0fe7-49d4-b576-4a972ae0f8b0)

### Checking Permissions on Mounted NFS Share

Upon checking the permissions on the mounted NFS share, we observe that only owner `1003` and group `1003` have access.

To address this, we create a user on our local machine and assign appropriate permissions.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/455a2ca3-9d71-447c-9d13-b41a89d53d65)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/d4fb36c6-21d8-4f75-aebb-b9d561fd4a6b)

**Accessing the Mounted NFS Share**

After logging in as the new user `hijackuser` with the correct permissions, we are able to read the contents of the directory.


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/cece2e93-7bcf-4609-a2ca-a1dae0f09741)

**Discovery in NFS Share**

Within the NFS share, we discover a file named `for_emplyees.txt`.

Upon reading this file, we find the following credentials. Let's use them to log in to the FTP server.

ftpuser:W3stV1rg1n14M0un741nM4m4

### RECON\ftp_2

**Logging in with Discovered Credentials**

Now that we have the credentials, we can proceed to log in.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/9cecd2c2-2178-4a12-b80e-2994546d2624)


### Retrieving Files from FTP Server

We notice two interesting files on the FTP server:
- `.from_admin.txt`
- `.passwords_list.txt`

Let's download both of these files to our local machine and examine if they contain valuable information.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/a422d85b-b873-4f39-b68f-1c8b4b48f002)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/26a0d617-f7a5-42c7-9248-a426272e1028)

**Analysis of Retrieved Files**

In the file `.from_admin.txt`, we notice something interesting mentioned at the bottom: brute-forcing the login form might not be the quickest route.

Regarding the file `.passwords_list.txt`, as expected, we find password hashes. Now, the question is, what's our next step?

### RECON\cookie

**Analysis of User Cookie**

Upon inspecting our own cookie for the user `hijackuser` and performing a base64 decode, we uncover something intriguing.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/020941b2-0fc0-4ced-9fa0-78905feb1a79)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/4a6221b7-5ad7-4f16-958d-eb71995c3fe3)

**Authentication via Cookie**

It appears that the username and password are passed as authentication via the cookie.

Upon running the hash behind the username through `hash-identifier`, we determine that it is an MD5 hash.


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/aa54defe-7ae2-40c5-be08-352fdddb741f)

**Verifying Authentication via Cookie**

To verify the hypothesis that the cookie also serves as authentication, I convert the password of the user `hijack` into an MD5 hash. If the converted MD5 hash matches the MD5 hash in the cookie, then we are on the right track.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/0034de65-26e1-4af0-99c5-a4d1a374362f)

**Verification Result**

As the screenshot above demonstrates, both hashes match.

We can now proceed with the exploitation phase of this box.

----------------------
----------------------

## Exploit

### EXPLOIT\cookie

**Generating MD5 Base64 Cookies Script**

Let's get to work with all this information. We need a script that converts all passwords in the `.passwords_list.txt` file into a list of accepted cookies, which can then be fired with `wfuzz` at the `administration.php` page.

I've named the script `md5_base64_cookie_gen.py` and it looks like this:


```python
import hashlib
import base64

# Open the input file and read its lines
with open('input_passwords.txt', 'r', encoding='utf-8') as input_file:
    input_lines = input_file.readlines()

# Open the output file to write the modified hashes
with open('output_hashes.txt', 'w', encoding='utf-8') as output_file:
    # Loop through the lines in the input file and process each line
    for line in input_lines:
        # Remove any non-alphanumeric characters from the line
        cleaned_line = ''.join(filter(str.isalnum, line))
        # Calculate the MD5 hash of the cleaned line
        hashed_line = hashlib.md5(cleaned_line.encode('utf-8')).hexdigest()
        # Prepend "admin:" to the hash
        modified_hash = 'admin:' + hashed_line
        # Encode the modified hash to Base64
        encoded_hash = base64.b64encode(modified_hash.encode('utf-8'))
        # Write the encoded hash to the output file
        output_file.write(encoded_hash.decode('utf-8') + '\n')
```

**Using Wfuzz for Cookie Brute Forcing**

As discussed above, I'll use `wfuzz` for this task. The following flags will be used:

- `-X POST`: Sending a POST request
- `-w`: Wordlist containing cookies
- `-b`: Location where the wordlist should be applied

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e310bf82-b00b-4243-8e98-5286698869ee)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/73937d5d-0d21-4f4f-84d9-a50329c17cfc)

**Successful Cookie Found**

We have a hit! The cookie accepted above is the admin cookie.

Let's apply this immediately.


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/cd7fb0f1-4617-4cd8-9ad1-b94c04094c10)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3ac54346-171b-401e-9e5c-f5d790ab91d9)


**Accessing Service Control Panel**

As the screenshot indicates, we have accessed a panel where we can check whether services are active or not. This likely means there is a shell with the web server itself. Perhaps it's possible to concatenate commands or loop through them.


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/c8739eec-374c-4fa7-be20-178a5acda32c)


**Leveraging Reverse Shell**

Since `;` and `|` do not work as expected, but `&` does, we'll aim for a reverse shell to gain more control.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/8f54cec2-f93f-4d7f-9812-4bbd9504278b)


### EXPLOIT\reverse_shell

**Setting Up Reverse Bash Shell**

Let's open a reverse bash shell to our local machine.

From the website [https://www.revshells.com/](https://www.revshells.com/), I'll obtain the bash shell and paste it into the web panel form. Before hitting enter, we'll start listening with `netcat` on port 9002.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/2c270408-9136-4721-9fd6-ab3ea2e3576c)


**Successful Connection with Reverse Shell**

And yes, we have established a connection with the server via a reverse shell.

Let's proceed to search for the `user` flag.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/1946e062-5885-41fa-88ee-6eabe5708f71)

**Accessing config.php**

As expected, we do not have access to the file `user.txt` in Rick's home directory.

However, the output of the Gobuster scan revealed the existence of a `config.php` file on the web server, which we previously couldn't access. Let's read that file; perhaps we'll find something juicy there.


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/b59ecf6d-c5aa-42ad-b576-e0a030f02747)


**Upgrading Shell for `su`**

We have found a password for the user `rick`: `rick::N3v3rG0nn4G1v3Y0uUp`.

To use `su`, we need to upgrade our shell. A simple Python bash shell will do wonders.

```python
python -c 'import pty; pty.spawn("/bin/bash")'

```

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/8648ff65-8d99-4ac7-bd39-8ec11485ff25)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/86f77b76-f237-4dc9-b141-d24cbe0fca10)



**Obtaining First Flag**

We have finally obtained the first flag! We can now cross `user.txt` off our list and move on to `root.txt`.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/a7cf8ade-d7db-4b37-af99-20e708c90a37)


## PRIV_ESC

### PRIV_ESC\sudo-l

**Checking Sudo Permissions**

Now, we need to obtain `root` privileges to read the root flag.

Perhaps there's a misconfiguration, so let's execute `sudo -l` to see if there are any programs that we can run as `rick` with root privileges.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/eba2e0c9-5523-4b6f-b797-9df594a81a2c)

**LD_PRELOAD Environment Variable Exploitation**

We notice that an environment variable can be invoked that should grant root privileges.

On the website Hacktricks, there is an item about this: [LD_PRELOAD and LD_LIBRARY_PATH](https://book.hacktricks.xyz/linux-hardening/privilege-escalation#ld_preload-and-ld_library_path)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/40e1d340-c3a7-4dd3-82a2-dc5d8e21d21d)

**Identifying Libraries Used by Apache2**

First, we need to determine which libraries are used by Apache2 so that we can abuse their names.


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e19e6e0e-18b8-4a88-8d87-eca1bc8ca0a9)

**Completing Privilege Escalation**

Now that we know which libraries are being used, we can further complete our privilege escalation.

According to Hacktricks, we need to create a `.c` file with the content found on the page of Hacktricks. Afterward, we compile it with `gcc`.


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/eb570ff0-583d-4456-9040-ba0f4c47a60f)

## Final Steps for Privilege Escalation

After compiling, we have two files in the `/tmp` folder:
- `priv.c`
- `libcrypt.so.1`

Now, if we combine this with the information from the command `sudo -l`, we'll get a root shell. :):):)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e6456683-05f3-4d8b-a4ac-48a3f9cbae12)


## Obtaining Root Flag

Now that we have obtained root privileges, we can finally read the last flag, the root flag, and thus, the box is popped and complete.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e110ebdf-3fcd-4ed4-99ab-b1e547eee2a8)


## Summary:

1. **Nmap Scan:**
   Conducted a thorough Nmap scan to identify open ports and services on the target machine.

2. **Credentials Discovery:**
   Discovered credentials in an NFS share, providing a potential entry point.

3. **Web Server Access:**
   Utilized the obtained credentials to gain access to the web server, uncovering further avenues for exploitation.

4. **Cookie Brute-Forcing:**
   Leveraged cookie brute-forcing techniques to escalate privileges and gain admin access on the web server.

5. **Service Control Panel Exploration:**
   Explored a service control panel, revealing a misconfigured environment variable and a path to privilege escalation.

6. **Privilege Escalation:**
   Crafted and executed a tailored exploit using LD_LIBRARY_PATH, exploiting the misconfigured environment variable to escalate privileges to root.

7. **Root Access:**
   Achieved root privileges, enabling the retrieval of both user and root flags, effectively completing the challenge.

