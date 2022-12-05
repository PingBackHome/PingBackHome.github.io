---
layout: post
title: TryHackMe | Advent of Cyber 2022
categories: TryHackMe
---

Start date: 05-12

# Day 3:

## Questions and Answers

What is the name of the Registrar for the domain santagift.shop?\
![image](https://user-images.githubusercontent.com/115549820/205648959-9012a375-87ea-4117-ba25-3bbb9bb0e5ff.png)
> Namecheap, Inc
-----------------------------

<br>
Find the website's source code (repository) on github.com and open the file containing sensitive credentials. Can you find the flag?\

![image](https://user-images.githubusercontent.com/115549820/205651105-4a4e46ac-ec3b-46a9-842a-965cd5c412ad.png)
> {THM_OSINT_WORKS}
-----------------------------


What is the name of the file containing passwords?
> config.php
-----------------------------


What is the name of the QA server associated with the website?\
![image](https://user-images.githubusercontent.com/115549820/205651747-467a420c-c11d-46b5-b676-0c568238e53a.png)
> qa.santagift.shop
-----------------------------


What is the DB_PASSWORD that is being reused between the QA and PROD environments?\
![image](https://user-images.githubusercontent.com/115549820/205652081-e2290f0f-b25b-4855-8dc2-89d94a54fa2e.png)
> S@nta2022
-----------------------------

