---
layout: post
title: TryHackMe | Glitch
categories: THM
---



# TryHackMe | Glitch
+++++++++++++++++++++++++++++++++++\
IP: 10.10.32.249\
Date: 03-05-2023\
+++++++++++++++++++++++++++++++++++

##  Fase 1: Recon

### Nmap scan

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235873551-fb9f9b86-c65c-4e8e-8836-704e9f5c9a6e.png">

**Open Ports**

80 - HTTP - nginx 1.14.0

### Webserver Enumeration

**Dirbuster output**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235881682-fae811e9-5e7e-4f3e-9629-d98143397908.png">

**Screenshot homepage**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235880562-136eef65-6ae3-4d3a-855d-7edab002edfa.png">

**Source code**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235880755-a3368dd6-a2a7-4703-b121-457282be5cca.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235880857-6ca75276-f175-42e1-a956-01206333193c.png">

**playing with getAccess()**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235882043-5f8f78d7-48f2-40a9-8065-7ce7948ab719.png">

**decoce base64 string**

<img width="400" alt="image" src="https://user-images.githubusercontent.com/115549820/235882830-f9e0422f-230d-463a-a4f0-ea555ce4c4db.png">

**Cookie value**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235883959-326edfd9-33a6-4814-80c8-1416baa703a2.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235884830-ea456613-a906-4a65-9d9d-a9cfc21e133d.png">

**Refresh page**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235884929-96ebb856-dcd5-43e0-87ad-73f9470828d3.png">

**Source code**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235885167-8d446652-14c8-4608-81b1-3359b6133ce4.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235885481-99108cf0-4b7b-4f80-aa8c-0869fdef12aa.png">

**script.js**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235885712-d7bd52db-89d8-46e4-ae94-ad2cb81c2a21.png">

**/api/items**

<img width="1192" alt="image" src="https://user-images.githubusercontent.com/115549820/235896171-d5f80738-1dec-4495-9636-2d215171c387.png">

**Fuzzing url**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235898112-89b2adbf-a03e-4786-9645-bbb44eb8c9a3.png">

**Check /api/items?cmd**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235900254-c8f26cc9-5f3c-4d50-b5ad-a951b412874d.png">


## Fase 2: Getting Access

**Reverse shell??**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235900639-12bd759f-00a4-4b43-9ce1-4089be607647.png">

<img width="350" alt="image" src="https://user-images.githubusercontent.com/115549820/235900824-d84b8572-3e57-4582-a5d6-61ff9f31533f.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235903559-7240791d-d369-465e-9b1a-3775817a8c41.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235903665-cadd4fd2-e000-49ac-bd07-9e28440385e4.png">

  
## Fase 3: Intern Enumeration

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235904016-56b5bb09-2b2b-48a9-af48-21d44a36ce4e.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235904807-023b1bfb-da8b-4e22-898e-8979e9b6ba1f.png">

**LinEnum report**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235906444-6f3c2c9d-4be0-4caf-88b0-1fefc8c46290.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235908093-61c9f93c-b268-48db-891d-d8b5dce15011.png">

**.firefox credentials**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235916611-a10c15d3-1544-4532-aab4-36f132d50b60.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235916665-7234834a-6419-42de-b0dc-e583ecd1e9c9.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235917037-eb15ad6a-4505-479c-893b-407b2487c42d.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235924174-b92cef46-df2a-4343-92f9-98266272f82a.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235924244-0f28304d-add8-4358-bb5e-7e3117e4008e.png">

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235924336-dcd3fd44-915b-4ddb-9db9-71235455350c.png">

**Upgrade shell**

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235925316-617ca890-72e5-4808-b54d-705d7369532f.png">

## Fase 4: PrivEsc

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115549820/235925588-1f83c467-316c-43fa-b2bf-d06d2e371a0d.png">

<img width="510" alt="image" src="https://user-images.githubusercontent.com/115549820/235925788-e8305da8-3dc7-4760-b206-d593a499aee8.png">

<img width="510" alt="image" src="https://user-images.githubusercontent.com/115549820/235926035-20d70995-b5dc-4c50-b9c2-9b615ad04f65.png">

<img width="510" alt="image" src="https://user-images.githubusercontent.com/115549820/235926236-9fabfd77-4b81-4e10-93f8-b32429175d07.png">

<img width="510" alt="image" src="https://user-images.githubusercontent.com/115549820/235926805-33e720db-2892-428c-9497-6303cc027129.png">

<img width="510" alt="image" src="https://user-images.githubusercontent.com/115549820/235926995-40bd3449-157a-4ae2-af08-5414fc6b2b89.png">

<img width="510" alt="image" src="https://user-images.githubusercontent.com/115549820/235927099-f9cd12ff-d30a-46de-a31b-6a7e112415ef.png">

  
## TryHackMe Questions

Deploy the machine.
> Done

What is your access token?
> this_is_not_real

What is the content of user.txt?
> THM{i_don't_know_why}

What is the content of root.txt?
> THM{diamonds_break_our_aching_minds}
