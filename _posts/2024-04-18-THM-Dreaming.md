---
layout: post
title: TryHackMe | Dreaming
categories: THM
---

_
In this CTF challenge, we embarked on a journey of enumeration, exploitation, and privilege escalation to uncover hidden flags and complete the mission._


## Recon

### Recon\nmap

We start as usual with an nmap scan over the IPv4 address we have obtained. I use the following parameters in my command:
- `-sV`: Service version detection
- `-sC`: Script scanning using default scripts
- `-A`: Aggressive mode, including OS detection, version detection, script scanning, and traceroute

Below you will find the result:

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/dba1a075-4de2-408e-ae4e-c37d3ad2251f)

As you can see in the output, we only have two active open ports:
- Port 22: SSH
- Port 80: Web server


### Recon\port 80

Let's start with the web server.\
When we open the webpage in the web browser, we see the default Apache web server page.\
There isn't much to find here yet, and there's also nothing in the source code.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3b3e69e7-80af-4a1a-9240-bdee4bfb2e98)


The next logical step is to investigate if there are any pages to visit.\
For this, I'll use `gobuster` as a tool.\
I'll be using the following parameters:
- `-w`: Wordlist for directory/file brute force
- `-o`: Output file to save results

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/7cacfa0f-dac7-4894-b357-d273fd2d6184)

The output only shows one page we can visit: `<host>/app`.\
Let's take a closer look at this one.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/8dce1292-d66b-46f9-b134-0801ddbe3c50)

On the `/app` page, there is a directory named `pluck-4.7.13`.\
When we open this directory, we land on the page below.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/fdb6225c-9fc8-4fa4-813a-71bf4bf102ff)

There isn't much to do on this page.\
However, we do have a hyperlink below the admin section. It can't hurt to take a look at this.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/cc57729b-3512-4789-ae6f-d9dfa7bfe9cc)

Now we're on a login page where we can only enter a password.\
Let's try the low-hanging fruit manually first. If this doesn't work, we can always resort to brute force techniques.
Passwords to try:
- admin
- welcome
- password

"password" was the correct guess! :)\
Now let's further explore if we can find anything on the admin panel.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/c932bc07-8dee-4a97-899f-4485572f5ab7)

Just to be sure, I'll start another gobuster, but this time from the point `/app/pluck-4.7.13/`.\
Who knows, it might give us more information.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/c3bfeb41-24c8-4dc2-a906-07d792c1cd36)

The latest gobuster scan gives the following entries:
- image
- files
- docs
- data
  
Let's start with "docs". Who knows, maybe there's some information about the web application and/or misconfigurations.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/42762465-122b-41a8-96b9-719db82576bf)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/6025f699-f3cb-464d-a7a0-55734d5c627d)

It wouldn't hurt to take a look at the changes and see if there are any old exploits we might still be able to reuse.\
But so far, there's no additional information that we can use.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/d180e146-30d2-4b07-855b-faeae8a891b0)

As you can see in the screenshot below, there is a possibility to upload objects.\
I've tried multiple reverse shells, but unfortunately, the application adds a .txt extension to the uploaded item.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e857b8c1-dd12-455c-ba7b-541a0909ed04)

Let's run the application `pluck` through `searchsploit` and see if it comes back with a known exploit.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/59a6c418-9d12-44a7-9a5b-ca418e3fe6df)

And there it is, we found one! See the highlighted exploit: 49909.py.


## Exploit

### Exploit\shell_upload

If we open 49909.py in a text editor like Sublime, we can see what syntax we should use to utilize the exploit.\
See the highlighted text in the screenshot below.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/a86c90ea-4627-4f07-ba82-adc3c349fe4b)

The syntax for this exploit is as follows:\
`<ip_address> <port> <admin_panel_password> <pluck_cmd_path>`

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3352d360-5f35-4ede-a6ec-1a6d43b2db99)

If we execute this exploit, we'll get a web shell. See the screenshot below for an example.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/9bac2fa2-5dc6-4bff-8b7d-c969371b3a7b)


After some manual enumeration, I discovered that there are some items in the `/opt` folder.\
We only have permissions to read `test.py`, so let's do that.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/0300250a-abcf-4ea6-9e49-1e00ec18b3ee)

Now that we have a username and password, we can try to log in via SSH with the username `lucien`.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/7f8af758-9503-4379-ab60-399a85d82887)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/219d3b4a-f9b3-43d8-b751-b5d6e5b66047)

And yes, we're in! Let's further investigate what we can find under the user `lucien`. Let's read the first flag.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/ef70e45a-98d0-46dc-875f-97a0fe2cc638)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/601f4f78-c0da-41ab-bf6f-b08eaa29db08)

## Privilege Escalation

### Privilege Escalation\sudo-l

We have the first flag. Let's see if we can escalate privileges to a user with more rights.
We can use the command `sudo -l` to see if we can do anything.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/216b610f-cb3f-4019-86d5-bea02b2f13b0)

We can use `getDreams.py` to perform privilege escalation.\
Let's give that a try.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/734b5d07-b562-4823-8fcd-1fe81778b901)

Unfortunately, that didn't work. So let's get `linpeas.sh` onto the host and use it to scan the machine for misconfigurations.


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/a8731676-b051-4e81-b30b-f12c306364e7)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3ef31300-ed38-432a-a79c-fd35f7f6fe83)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/870f38ca-5682-43c4-a165-0fe167d975d4)

We see in the bash history of the user `lucien` that they connected to MySQL and we see a plaintext password.
Let's take a look at the script `getDreams.py` in the folder `/opt` and see if we can do something with it.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/4273f7e3-e313-4c59-b5c3-bd6ee77e8e41)

We see in the `else` statement that a shell can be invoked, which we could theoretically abuse. Furthermore, we see that the script uses an SQL instance, and we know that the user `lucien` has used MySQL. Let's further investigate this.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/26b6bddd-db14-4a82-b231-6391e7ee26d6)

Now that we're logged into MySQL as the user `lucien`, we need to look around to see which databases exist and which tables are present.


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/d3341285-4a39-4868-af27-5bf44103fbc3)

We have multiple databases, but we're only interested in the `library` database.\ 
Let's select this one, and when we read the tables, we see 2 columns (`dreamer`, `dreams`) with multiple rows.\ 
We're on the right track. If you scroll back to `getDreams.py`, you'll see that two columns are being called: `dreamer` and `dreams`.

We know that a shell can be invoked, so let's get a standard reverse shell from the website https://www.revshells.com. \ 
Also, let's start a netcat listener on port 9001.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/35a021fc-7c46-4fd0-8337-40bd89119601)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/29b7a683-a8b5-4be2-80e3-b650c3119d70)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3ef120d6-ad61-4843-a6a9-3f209a5eaf03)

As you can see in the screenshot below, we have a successful connection :)\
Let's read the flag of the user `death` and continue with enumeration.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/a9f9a531-4974-4984-84b1-cf12bb0962c8)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/d6a351b2-da4c-4dba-bb08-6ab0f91421e6)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/2124d9bd-d59a-442d-b0b1-b2d519a8f436)

In the home folder of the user `death`, we also find a script named `getDreams.py`.\
When we read this script, we see a database password for the user `death`.\
In this box, passwords are used in multiple places at once. Maybe we can also log in as the user `death` with this password.


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/2124d9bd-d59a-442d-b0b1-b2d519a8f436)

We are now logged in as the user `death`. Let's navigate to the home folder of the user.\ 
Who knows, we might find something interesting there.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/b41aa595-b703-419c-a7ff-a5348c5017bd)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/7a919260-3849-4cbd-a188-23430adb0096)

If we read the script `restore.py`, we see that backups are being made and that a library is being imported.\
Let's see if we can abuse this :):):)

Let's search for this library on the machine. I'll use the `find` command with the following parameters:
- `type f`
- `group death`
- `name shutil`
- `ls`

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/2a186a2b-f433-4c2a-8c22-375df7e3ca79)

We see in the output that the library is owned by `root` and that the group `death` also has access to it. 
So, we can do something with this :)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3c8a7436-30c1-47d9-8b39-1f1d27a0b7a5)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/f1dd5e9c-4d7c-4b8b-807a-1d764458402a)

If we open `shutil.py` in a text editor and search for `copy2`, we can place a reverse shell in the script. 
We'll also get this from revshells.com.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/1ab58528-0a7b-4b2b-8db6-884f7037cf50)

And now we have a connection as the user `morpheus`. 
Let's read the last flag; we've managed to collect all the flags.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/ac83ad7a-682b-4448-8820-f4bb68e296e6)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/03670bb3-119a-492c-9f30-7e5312ceaf9e)


## Summary of CTF Challenge

1. **Enumeration:**
   - Conducted an nmap scan to identify open ports and services.

2. **Web Exploration:**
   - Discovered a web server and used gobuster to explore directories.

3. **Exploitation Attempts:**
   - Attempted to exploit an upload feature, but encountered file extension limitation.

4. **Exploit Discovery:**
   - Found a known exploit for the application `pluck` using searchsploit.

5. **Initial Exploitation:**
   - Successfully exploited `pluck`, gained a web shell, and escalated privileges.

6. **Credential Discovery:**
   - Discovered credentials in MySQL and utilized them to SSH into the system.

7. **Privilege Escalation:**
   - Explored the file system, found another script, and escalated privileges further.

8. **Library Vulnerability:**
   - Leveraged a vulnerability in a system library to gain a reverse shell as another user.

9. **Completion:**
   - Successfully collected all the flags and completed the challenge!


