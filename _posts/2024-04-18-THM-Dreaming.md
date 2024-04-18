---
layout: post
title: TryHackMe | Dreaming
categories: THM
---


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

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3b3e69e7-80af-4a1a-9240-bdee4bfb2e98)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/7cacfa0f-dac7-4894-b357-d273fd2d6184)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/8dce1292-d66b-46f9-b134-0801ddbe3c50)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/fdb6225c-9fc8-4fa4-813a-71bf4bf102ff)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/cc57729b-3512-4789-ae6f-d9dfa7bfe9cc)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/c932bc07-8dee-4a97-899f-4485572f5ab7)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/c3bfeb41-24c8-4dc2-a906-07d792c1cd36)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/42762465-122b-41a8-96b9-719db82576bf)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/6025f699-f3cb-464d-a7a0-55734d5c627d)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/d180e146-30d2-4b07-855b-faeae8a891b0)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e857b8c1-dd12-455c-ba7b-541a0909ed04)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/59a6c418-9d12-44a7-9a5b-ca418e3fe6df)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3352d360-5f35-4ede-a6ec-1a6d43b2db99)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/9bac2fa2-5dc6-4bff-8b7d-c969371b3a7b)



![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/7896eef1-b61b-4c0a-aac9-d09ed3ea163e)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/088c972e-4cb7-41cb-9ae9-521d69f047b8)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/07d40a3f-132e-4f75-a555-66963d58f068)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/c8404beb-471b-42f8-b7bf-f913100a097b)



![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/fe3adf2c-b373-4d3d-a816-98b895955d8a)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/0300250a-abcf-4ea6-9e49-1e00ec18b3ee)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/27939003-66eb-4494-a3dc-a027ea127bec)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/7f8af758-9503-4379-ab60-399a85d82887)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/219d3b4a-f9b3-43d8-b751-b5d6e5b66047)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/ef70e45a-98d0-46dc-875f-97a0fe2cc638)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/601f4f78-c0da-41ab-bf6f-b08eaa29db08)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/216b610f-cb3f-4019-86d5-bea02b2f13b0)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/734b5d07-b562-4823-8fcd-1fe81778b901)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/a8731676-b051-4e81-b30b-f12c306364e7)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3ef31300-ed38-432a-a79c-fd35f7f6fe83)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/870f38ca-5682-43c4-a165-0fe167d975d4)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/8d91916a-bf7a-400c-9d19-ce18ef3909b8)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/e80ea9c3-b5a5-4f4c-bffc-baa66286b509)



![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/4273f7e3-e313-4c59-b5c3-bd6ee77e8e41)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/26b6bddd-db14-4a82-b231-6391e7ee26d6)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/d3aa7587-9439-4fbf-b574-c3f99aa6374f)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/b57f7fa4-09e8-45dd-a6cf-5d050f2a0000)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/29b7a683-a8b5-4be2-80e3-b650c3119d70)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/d3341285-4a39-4868-af27-5bf44103fbc3)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/08b4141b-8fba-474f-878f-8f58bb30dd0c)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/c221e6fb-ea6d-491a-bb19-95d2b99a9391)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/7e459e16-ec14-4fa7-95c8-0a2ebbc13b36)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/adef7b19-26eb-490c-bb8e-9769bb4df3b3)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/35a021fc-7c46-4fd0-8337-40bd89119601)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3ef120d6-ad61-4843-a6a9-3f209a5eaf03)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/a9f9a531-4974-4984-84b1-cf12bb0962c8)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/d6a351b2-da4c-4dba-bb08-6ab0f91421e6)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/ec488c1f-691a-4e23-b962-d7d69b121866)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/2124d9bd-d59a-442d-b0b1-b2d519a8f436)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/b41aa595-b703-419c-a7ff-a5348c5017bd)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/7a919260-3849-4cbd-a188-23430adb0096)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/2a186a2b-f433-4c2a-8c22-375df7e3ca79)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/3c8a7436-30c1-47d9-8b39-1f1d27a0b7a5)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/ac83ad7a-682b-4448-8820-f4bb68e296e6)

![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/1ab58528-0a7b-4b2b-8db6-884f7037cf50)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/f1dd5e9c-4d7c-4b8b-807a-1d764458402a)


![afbeelding](https://github.com/PingBackHome/PingBackHome.github.io/assets/115549820/03670bb3-119a-492c-9f30-7e5312ceaf9e)
