---
layout: post
title: TryHackMe | Advent of Cyber 2022 - Day 6
categories: TryHackMe
---

Start date 07-12

# Day 6:

## Questions and Answers

What is the email address of the sender?\
<img width="633" alt="image" src="https://user-images.githubusercontent.com/115549820/206134549-5703efbd-2f4f-485d-80f0-b7d85e0a6317.png">
> chief.elf@santaclaus.thm


What is the return address?\
<img width="587" alt="image" src="https://user-images.githubusercontent.com/115549820/206138006-d7e5746e-f8b5-4e54-a8ba-ce4f00a1fefe.png">
> murphy.evident@bandityeti.thm


On whose behalf was the email sent?\
<img width="587" alt="image" src="https://user-images.githubusercontent.com/115549820/206138314-bb0f3e03-0a70-4b12-a30f-5d047f250d81.png">
> Chief Elf


What is the X-spam score?\
<img width="587" alt="image" src="https://user-images.githubusercontent.com/115549820/206139169-02eefdbf-5b14-4d5e-8970-38a2acd1e25b.png">
> 3


What is hidden in the value of the Message-ID field?\
<img width="633" alt="image" src="https://user-images.githubusercontent.com/115549820/206142769-3091bf15-9eb0-4c43-933c-3688ccf58646.png">
<img width="633" alt="image" src="https://user-images.githubusercontent.com/115549820/206143096-ca9f8b49-2f75-4959-ac42-8d3749f278aa.png">
> AoC2022_Email_Analysis


Visit the email reputation check website provided in the task.\
What is the reputation result of the sender's email address?\
<img width="1113" alt="image" src="https://user-images.githubusercontent.com/115549820/206143644-34f7a6d4-e203-4c04-85a3-a6ad807926fb.png">
> RISKY


Check the attachments.\
What is the filename of the attachment?\
<img width="534" alt="image" src="https://user-images.githubusercontent.com/115549820/206144088-8fdc7711-c6ce-4a9b-96c3-53753f6689da.png">
> Division_of_labour-Load_share_plan.doc


What is the hash value of the attachment?





Visit the Virus Total website and use the hash value to search.
Navigate to the behaviour section.
What is the second tactic marked in the Mitre ATT&CK section?



Visit the InQuest website and use the hash value to search.
What is the subcategory of the file?
