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

____________________________________________

What is the return address?\
<img width="587" alt="image" src="https://user-images.githubusercontent.com/115549820/206138006-d7e5746e-f8b5-4e54-a8ba-ce4f00a1fefe.png">
> murphy.evident@bandityeti.thm

____________________________________________

On whose behalf was the email sent?\
<img width="587" alt="image" src="https://user-images.githubusercontent.com/115549820/206138314-bb0f3e03-0a70-4b12-a30f-5d047f250d81.png">
> Chief Elf

____________________________________________

What is the X-spam score?\
<img width="587" alt="image" src="https://user-images.githubusercontent.com/115549820/206139169-02eefdbf-5b14-4d5e-8970-38a2acd1e25b.png">
> 3

____________________________________________

What is hidden in the value of the Message-ID field?\
<img width="633" alt="image" src="https://user-images.githubusercontent.com/115549820/206142769-3091bf15-9eb0-4c43-933c-3688ccf58646.png">
<img width="633" alt="image" src="https://user-images.githubusercontent.com/115549820/206143096-ca9f8b49-2f75-4959-ac42-8d3749f278aa.png">
> AoC2022_Email_Analysis

____________________________________________

Visit the email reputation check website provided in the task.\
What is the reputation result of the sender's email address?\
<img width="1113" alt="image" src="https://user-images.githubusercontent.com/115549820/206143644-34f7a6d4-e203-4c04-85a3-a6ad807926fb.png">
> RISKY

____________________________________________

Check the attachments.\
What is the filename of the attachment?\
<img width="534" alt="image" src="https://user-images.githubusercontent.com/115549820/206144088-8fdc7711-c6ce-4a9b-96c3-53753f6689da.png">
> Division_of_labour-Load_share_plan.doc

____________________________________________

What is the hash value of the attachment?\
<img width="632" alt="image" src="https://user-images.githubusercontent.com/115549820/206147975-0621ad7d-62e3-4aa3-a6d4-aaa7bf2d8aa8.png">
> 0827bb9a2e7c0628b82256759f0f888ca1abd6a2d903acdb8e44aca6a1a03467

____________________________________________

Visit the Virus Total website and use the hash value to search.\
Navigate to the behaviour section.\
What is the second tactic marked in the Mitre ATT&CK section?\
<img width="774" alt="image" src="https://user-images.githubusercontent.com/115549820/206150000-dbdbc9d0-cc6d-4f4f-8ac3-f09e61a2fb5e.png">
> Defense Evasion

____________________________________________

Visit the InQuest website and use the hash value to search.\
What is the subcategory of the file?\
<img width="1141" alt="image" src="https://user-images.githubusercontent.com/115549820/206148926-8cef3a1e-0c4e-4024-a616-084b92976e3e.png">
> macro_hunter

