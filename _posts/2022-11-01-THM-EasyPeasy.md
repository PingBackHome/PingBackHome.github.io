---
layout: post
title: TryHackMe | Easy Peasy
---

# TryHackMe | Easy Peasy

+++++++++++++++++++++++++++++++++++\
IP: 10.10.190.29\
Date: 01-11-2022\
+++++++++++++++++++++++++++++++++++

## Task 1: Enumeration through nmap
  
**1.1 How many ports are open?**\
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199221147-536ec83c-ee29-4a37-bc78-04bd9fca35e4.png">
> 3

**1.2 What is the version of nginx?**\
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199221380-e9d8425c-e4f8-4f5a-a0a9-f136265938d8.png">
> 1.16.1
  
**1.3 What is running on the highest port?**\
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199221482-644b5923-a3c7-4bcd-8a43-d83498234407.png">
> Apache

## Task 2: Compromising the machine

**2.1 Using Gobuster, find flag 1.**\
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199230370-8919f902-c96a-4c1d-a839-faaea1ebe3cb.png">
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199230489-c9d88b74-232a-46b8-8e61-e3dbd187d134.png">
> flag{f1rs7_fl4g}

**2.2 Further enumerate the machine, what is flag 2?**\
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199228565-c4cb9f4d-b01c-4f2a-b2a5-c465daff70b4.png">
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199228706-e285000d-5ee3-45a2-bb35-1f4e499a701c.png">
> flag{1m_s3c0nd_fl4g}

**2.3 Crack the hash with easypeasy.txt, What is the flag 3?**\
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199231247-cab1eb29-7726-4a9e-8c91-47b8849d6e31.png">
> flag{9fdafbd64c47471a8f54cd3fc64cd312}

**2.4 What is the hidden directory?**\
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199231456-311fb94e-a540-4b40-a0d7-f2c22e5a1da0.png">
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199231750-d8a3ad99-d57f-48f8-a79c-d3d35bb8e649.png">
> /n0th1ng3ls3m4tt3r

**2.5 Using the wordlist that provided to you in this task crack the hash, what is the password?**\
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199232095-cdf462a0-7ef6-47d8-a169-1a6361e060c8.png">
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199232986-f9a2806a-8173-400c-981d-9d30afab3505.png">
> mypasswordforthatjob

**2.6 What is the password to login to the machine via SSH?**\
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199233564-51a44c8b-03e0-4ca5-9ef6-bb38fdadf665.png">
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199233836-c171c257-0796-4246-80f5-66e03323f29d.png">
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199234005-d467a2c5-687f-4e04-bab4-5f65b2de4ca7.png">
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199234152-71e633b2-85f0-44c5-a585-ba7c5cff0632.png">
> iconvertedmypasswordtobinary

**2.7 What is the user flag?**\
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199234817-c5e5b278-8433-4a67-af98-f8e29d2ca573.png">
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199235193-ad1cc41c-8e8a-4466-b210-d381350e7437.png">
> flag{n0wits33msn0rm4l}

**2.8 What is the root flag?**\
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199236646-5a3d5c28-a827-4582-9222-c310cb3ace49.png">
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199237364-12f4f7d3-7236-40d6-ae76-eafa70ed3665.png">
<img width="300" alt="image" src="https://user-images.githubusercontent.com/115549820/199238439-05bc239c-64b2-439c-8873-c481cd1f6282.png">
> flag{63a9f0ea7bb98050796b649e85481845}

