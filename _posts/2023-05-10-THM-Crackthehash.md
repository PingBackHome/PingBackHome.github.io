---
layout: post
title: TryHackMe | Crack the hash
categories: THM
---

## Level 1

**Hash 1: 48bb6e862e54f2a795ffc4e541caed4d**

Today we do the assignments that come with 'Crack the hash', I assume that doesn't take a lot of effort. So let's start!
I always find it useful to place the hashes in a .txt file, you can do this with your default text editor. I use 'nano' for convenience.

Let's open nano with the file name hash1.txt for example and paste the first hash in the text document.

<img width="300" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/960aa329-5f1f-48f8-91aa-e5d87a447e97">

<img width="300" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/ceafd229-e951-477c-b10f-87a73d9f8fd5">

We first need to find out what hash this is, kali has built in tools to find out, let's use hash identifier.

<img width="300" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e84c2db7-7621-4da2-92f1-b5055226b942">

48bb6e862e54f2a795ffc4e541caed4d = MD5 hash

MD5 hashes can be cracked with John, another built-in program in Kali Linux.

In order for John to crack the MD5 hash, we need to use the following syntax:
john -format=raw-md5 /path/to/file

Where /path/to/file should be your hash1.txt file.

<img width="300" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/8f1a1338-4693-46ef-82fb-b1cbc9b6afc5">

Hash 1: 48bb6e862e54f2a795ffc4e541caed4d
> easy

--------------------------------------------------------------------

**Hash 2: CBFDAC6008F9CAB4083784CBD1874F76618D2A97**

Again we place the hash in a text document and check what kind of hash this is.

<img width="410" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/232b4c12-56e9-4899-9fef-e6bbb96791af">

Hashid indicates it's a SHA-1 hash, let's crack that one too.

Again we use John to crack the hash, we use different flags now.\
We will first use without wordlist and if that doesn't work then we will use the 'default' wordlist in Kali Linux.\
Syntax for without wordlist: john --single --format=raw-sha1 /path/to/file\
Syntax for wordlist: john --wordlist=/usr/share/wordlists/rockyou.txt

_without wordlist_

<img width="500" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/dedec41e-9d01-44ce-bda3-b5cf618a134f">

_with wordlist_

<img width="500" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e3234b66-b256-49a4-90d9-b3760d4a1b04">

Hash 2: CBFDAC6008F9CAB4083784CBD1874F76618D2A97
> password123

--------------------------------------------------------------------

**Hash 3: 1C8BFE8F801D79745C4631D09FFF36C82AA37FC4CCE4FC946683D7B336B63032**

We first place the hash in a text document, I like to use nano for simplicity.

<img width="300" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/81b7fe08-dc83-41ab-9f3b-1491700a597a">

And then use 'hash-identifier' to find what kind of hash this is.\
<img width="300" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e8e3e092-169f-4079-9ab1-5cd9adf53398">

We know it's SHA-256 now, let's use our multi-tool aka 'John' again to crack this.\
We use the '--format=raw-' flags as in the previous hashes, but then we specify that it is a SHA-256 hash.\
Also don't forget to include a wordlist, I use the default rockyou.txt as wordlist.\
<img width="300" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/0c1fddf3-0c4c-4da1-a65e-9402097c1a60">

Hash 3: 1C8BFE8F801D79745C4631D09FFF36C82AA37FC4CCE4FC946683D7B336B63032
> letmein

--------------------------------------------------------------------

**Hash 4: $2y$12$Dwt1BZj6pcyc3Dy1FWZ5ieeUznr71EeNkJkUlypTsgbX1H68wsRom**

Hash 4 is not recognized by hash identifier so I use hashid to find out what hash this could be.

<img width="300" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/f10ecf50-a839-4fa6-8342-110729a12af4">

As you can see in the screenshot above hashid returns: 'bcrypt'\
I also had to google whether bcrypt hashes can be cracked by 'John', the pentestmonkey site indicates that val can.\
See link for more explanation: https://pentestmonkey.net/cheat-sheet/john-the-ripper-hash-formats

To crack blowfish hashes we use the following syntax: john --format=bcrypt /path/to/hashfile\
Bcrypt hashes usually take a very long time, I'm currently cracking 5 minutes via 'John' and I'm only at 0.05%.\
<img width="300" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/1e1c6127-4eed-42c2-9fef-e3782dcd53ce">

Hash 4: $2y$12$Dwt1BZj6pcyc3Dy1FWZ5ieeUznr71EeNkJkUlypTsgbX1H68wsRom
> bleh

--------------------------------------------------------------------

**Hash 5: 279412f945939ba78ce0758d3fd83daa**

As before, let's first figure out what kind of hash this is.\
<img width="300" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/7be51788-307c-4224-ab58-c502516c9795">

<img width="300" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/5a17a55d-f286-4d73-af51-682630bb9380">

It is therefore an MD4 hash, MD4 and MD5 hashes are better done by an online cracking station, e.g. [crackstation.net](https://crackstation.net)

<img width="500" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3f0d67eb-4b13-45da-b1de-609c1f353c35">

Hash 5: 279412f945939ba78ce0758d3fd83daa
> Eternity22

--------------------------------------------------------------------

## Level 2

**Hash 6: F09EDCB1FCEFC6DFB23DC3505A882655FF77375ED8AA2D1C13F640FCCC2D0C85**

Using the hash-identifier tool, we find out that hash 6 is a SHA-256 hash.
<img width="500" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/9c168225-94eb-4c08-b1c1-7b7d74c73b25">

Hash 3 was also a SHA-256 hash, let's follow the same steps as with hash 3.\
Command: john --format=raw-sha256 hash6.txt --wordlist=/usr/share/wordlists/rockyou.txt

<img width="500" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/369de0e0-6a52-4270-9c4d-10e1460170ff">

Hash 6: F09EDCB1FCEFC6DFB23DC3505A882655FF77375ED8AA2D1C13F640FCCC2D0C85
> paule

--------------------------------------------------------------------

**Hash 7: 1DFECA0C002AE40B8619ECF94819CC1B**

When I try to identify the hash with 'hashid' or 'hash-identifier' I get different results :(\

<img width="500" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/24f15b78-d454-404c-9a62-dd488d64e9b9">\

<img width="500" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/ca0314b2-2da7-4189-8bb2-9cad958cc0b0">\

Fortunately, the online hash identifier does have a clear answer.\
<img width="500" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/bf451d95-044c-4c50-a92c-596e83d9ebe7">

Cracking NTLM on a laptop takes a long time...\
<img width="500" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/0e30af3e-1ee3-424b-9205-8178387642c9">

To be on the safe side, I check crackstation to see if they happen to have this hash in their database.\
<img width="500" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/0fae36eb-f287-4c70-b943-192ebde0c068">

Hash 7: 1DFECA0C002AE40B8619ECF94819CC1B
> n63umy8lkf4i

--------------------------------------------------------------------

**Hash 8:  $6$aReallyHardSalt$6WKUTqzq.UQQmrm0p/T7MPpMbGNnzXPMAXi4bJMl9be.cfi3/qxIf.hsGpS41BqMhSrHVXgMpdjS6xeKZAs02.\
  Salt: aReallyHardSalt**

<img width="500" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/26719650-b254-48cc-9ada-0fd4fa597fe1">

<img width="500" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/6a45a285-a576-41e4-9759-69143f0f2cc2">

<img width="961" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/51247357-bb1d-46f8-bfc9-d0937deb7472">

Hash 8: $6$aReallyHardSalt$6WKUTqzq.UQQmrm0p/T7MPpMbGNnzXPMAXi4bJMl9be.cfi3/qxIf.hsGpS41BqMhSrHVXgMpdjS6xeKZAs02.
> waka99



--------------------------------------------------------------------

**Hash 9: e5d8870e5bdd26602cab8dbe07a942c8669e56d6\
  Salt: tryhackme**

At the last hash see that the salt hasn't been added to the hash yet, let's do that first and put the hash+salt in a text document.

hash 9 + salt = e5d8870e5bdd26602cab8dbe07a942c8669e56d6:tryhackme

<img width="500" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/2608923f-c27e-4ec2-b671-81bdb7cf27a2">

<img width="961" alt="image" src="https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/9aefbfbb-70fc-4eaf-8c14-0fb3827207e9">

Hash 9: e5d8870e5bdd26602cab8dbe07a942c8669e56d6:tryhackme
> 481616481616




 







