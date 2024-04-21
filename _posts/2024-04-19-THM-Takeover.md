---
layout: post
title: TryHackMe | TakeOver
categories: THM
---



As the hint for this task suggests, it is important to modify our hosts file by adding the IP address and hostname of the box to it.


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/b3c0e69d-3d6e-4798-9cf3-6470983bf7ea)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e40ba9d1-62b0-4b8e-88ba-ddd0aebaab50)


##Recon

### Recon\nmap

Now that we have done this, we will proceed with our customary nmap scan over the box.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/20e9ac60-2b24-4bf9-b6b8-2c166dd01d6a)


We have multiple ports open: port 22 for SSH, port 80 for Apache HTTP, and port 443 for Apache HTTPS.

Let's start by examining what is present on the webserver.

**https://futurevera.thm**

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/628e9a03-f45e-49cb-b251-fbf8db0fb0ff)
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/97ebdc9b-e86b-4119-a55c-b561ae527084)

### Recon\gobuster

Let's also start a `gobuster` scan with flags `dir`, `vhost`, and a vhost with the flag `-k` for HTTPS.\
For the `dir` flag, I'll use the standard directory wordlist `dirbuster/directory-list-2.3-medium.txt`, and for `vhost`, `/usr/share/wordlists/dirb/big.txt`.

**dir\output**

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/7916b428-9f8e-497c-bb20-9e62488b39c2)

**vhost\output**

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/f33a0829-d6ad-42c7-92f6-e1abc9dfe23d)

**vhost_ssl\output**

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/991c135f-7109-477d-9649-838428ce0f67)

Okay, we have found several items:
- suport.futurevera.thm
- blog.futurevera.thm
- portal.futurevera.thm
- payroll.futurevera.thm

Let's add these subdomains to the hosts file and see if we can find anything interesting.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/66010fb4-a499-45ac-9f5e-f0478897bd81)


### Recon\subdomains

**blog.futurevera.thm**

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/531d8b50-5cb2-4349-bd08-44fbce5e8b56)
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/fc5cf002-adac-4532-929a-92095a4c6d97)
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/46816664-71c0-4bc9-86ba-4fbdced12985)


The subdomain "blog" displays a blog with 3 pages in the menu bar (Home, Blog, About Us).\ 
None of them seem interesting, and the source code doesn't reveal anything promising.

**payroll.futurevera.thm & portal.futurevera.thm**

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/4c29aba7-b9d0-4349-a4fc-9436ea624409)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/ac2a5a63-5519-4d39-bc87-d4245427e01a)

For the subdomains "payroll" and "portal," I'm redirected to the original homepage, so nothing particularly interesting there either.


**support.futurevera.thm**

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/fc575dfb-3cc8-4a00-9d0a-4188a07455bd)
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/fb740e66-da4a-4dee-99ca-e55ab939b123)

However, the "support" subdomain is a different story.

Who knows, perhaps gobuster from this point onward will yield something with the `dir` flag.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/1c236012-6b79-488e-8b81-f69be4087c15)

Unfortunately, that doesn't yield anything quickly. 
Perhaps the SSL certificate will reveal something.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/fbe55151-005f-4ab0-bb9e-c48c0efc185f)

Yes, this might be what we're looking for. See in the screenshot the following section: `Subject Alt Names`.
Let's add this subdomain to our hosts file as well.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/a79934bb-f42b-4376-afc8-90b88bdff9fa)

The HTTPS variant doesn't yield anything.
![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/6fe936df-ae8e-4a8b-961f-b31322b04361)


And the HTTP variant shows us the requested flag from TryHackMe.

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/4dd7f20d-73b7-415a-a30f-0953b4d7e607)

## Summary:

1. **Task Initiation:** 
   - Modified the hosts file as indicated in the task hint, adding the IP address and hostname of the box.

2. **Nmap Scan:** 
   - Conducted an Nmap scan over the box, revealing multiple open ports: 
     - Port 22 for SSH
     - Port 80 for Apache HTTP
     - Port 443 for Apache HTTPS.

3. **Web Server Analysis:** 
   - Explored the content on ports 80 and 443, finding a blog on port 80 with three pages (Home, Blog, About Us), but nothing of interest in the source code. 

4. **Gobuster Scan:** 
   - Launched a Gobuster scan with flags `dir`, `vhost`, and a vhost with the flag `-k` for HTTPS, using different wordlists for directories and vhosts.

5. **Subdomain Discovery:** 
   - Discovered several subdomains - "support," "blog," "portal," and "payroll."

6. **Exploration of Subdomains:** 
   - Investigated each subdomain's content. Found nothing significant on "blog," "portal," or "payroll," but "support" was noteworthy.

7. **Further Investigation:** 
   - Despite Gobuster not yielding immediate results, continued to explore the SSL certificate, finding potential leads in the "Subject Alt Names" section.

8. **Hosts File Update:** 
   - Added discovered subdomains to the hosts file for further investigation.

9. **Conclusion:** 
   - While the HTTPS variant didn't provide useful information, the HTTP variant revealed the requested flag from TryHackMe.

In summary, we conducted a thorough reconnaissance of the target, exploring open ports, subdomains, and web server content to uncover potential vulnerabilities and gather intelligence.
