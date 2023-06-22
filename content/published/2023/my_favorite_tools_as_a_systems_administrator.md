---
title: "My favorite tools as a systems administrator"
tags:
  - software
  - hardware
  - tools
  - utilities
---

# Introduction
Over the course of the early years of my career in IT, I've found and been introduced to various tools that make my job much easier. While the majority of systems admins have heard of or already use these, I wanted to share in case there are other sysadmins in the earlier years of their careers, or old hat admins who might just not have heard of them. Because who doesn't want their life to be a bit easier?

>[!info] Not Affiliated
>This post contains various links, and are *not* affiliate links. I have no relationship with these brands, and do not receive any compensation for these articles or links at the time of this post's writing.

# Software

## Devolutions Remote Desktop Manager
RDM is hands down my absolute favorite piece of software. It is far and away the best remote connection manager I've ever used. It feels like it is built by systems admins, for systems admins. The list of features in this software can't even really be talked about here, because it's so extensive. At a very reasonable (frankly low) price, you can manage all of your remote connections to just about anything conveniently and securely. I won't go into tons of detail here, but please for your benefit check out the link below and get a trial or use the free version for a bit to see how it can absolutely change your IT life.

[Link](https://devolutions.net/remote-desktop-manager/)

## Devolutions Server
DVLS is essentially a password manager for your remote connections. It interfaces with Remote Desktop Manager seamlessly and features Privileged Access Management to make maintaining IT security significantly easier, and enables you to empower less technical team members to resolve issues without permanently giving them additional permissions. It also has an inbuilt gateway functionality and you can use as a bastion server, which further increases security. It's a little bit involved to learn all the permissions and setup, but well worth it in the end. And the price is quite reasonable for what it is.

[Link](https://devolutions.net/server/)

## VSCode
Microsoft's Visual Studio Code is a fantastic and free tool for editing various file types that are common among systems administrators, be it PowerShell scripts, Shell scripts, XML, XAML, YAML, JSON, and more. With a ridiculously vibrant store of extensions, you can make connections to SQL servers, run queries, make API calls, manage resources in Azure, and so much more. 

For basic notepad use, I of course love Notepad++, but when it comes to scripting and anything that you'll work on for more than a couple of minutes, I highly recommend VSCode.

[Link](https://code.visualstudio.com/)

## ObsidianMD
Obsidian is a Markdown editor that is fantastic for notetaking and organizing your knowledge. As mentioned on the home page of this blog, there's plenty to learn and plenty to forget in IT. Obsidian is great because it can be as simple or as involved as you'd like. It is very low-friction to get started. It is free, and ultimately has no lock-in since your notes are just markdown files stored in a set of directories. I use this for daily notes, writing documentation, and even writing this blog.

[Link](https://obsidian.md/)

## Your choice of Large Language Model (LLM)
Large Language Models (LLMs) and artificial intelligence (AI) in general are becoming much more prominent and readily-accessible.  There are plenty of things they are great at accomplishing, but 
there are two reasons I recommend using one of your choice.

Firstly, they're better search engines (assuming they have access to the internet, unlike OpenAI's GPT-3). You'll likely find that you get significantly better results asking ChatGPT or Bard questions, as opposed to Googling them. That said, learning how to get what you want out of these LLMs is a science, and takes a bit of learning.

Secondly, they're surprisingly decent at writing you starter code. Teams I've worked with have utilized it to write out the beginnings of switch configurations, PowerShell scripts, Ansible playbooks, etc. Of course, the LLMs will get things wrong and you certainly need to go over everything they generate, but they'll get you pretty close, very quickly.

This is going to be the way of the future, so we might as well embrace it now!

[OpenAI ChatGPT](https://openai.com/blog/chatgpt) | [Google Bard](https://bard.google.com/) | And others...

# Hardware

## StarTech USB Crash Cart Adapter
In my first year as a systems administrator, I spent a lot of time propping 4:3 monitors up against server racks and balancing USB keyboards on my hand while trying to type, since we didn't really have rack-mounted KVMs anymore. That got old real quick! I went searching for a solution to this problem. Enter the StarTech USB Crash Cart Adapter.

This little package connects to your laptop via USB, and then connects to the server via VGA and USB. Using the included software, you will get the server's video output in a window on your screen, and you can use your laptop to control the server. This is a lifesaver in "break-glass" situations where things have gone very sideways, situations where the network is unavailable, or when you need to do initial setup on a host or array where the IPMI is not connected yet.

This thing comes in around $500 USD, but sure beats doing what I was doing previously. Obviously it's slightly less valuable to those who have rack-mounted KVMs in every rack, consistently. But if you don't, this is for you!

[Link](https://www.amazon.com/StarTech-com-Console-Portable-Adapter-Transfer/dp/B00IZGR6IK/ref=sr_1_4?crid=DXUA9HM1222Y&keywords=startech+crash+cart+adapter&qid=1687409352&s=electronics&sprefix=startech+crash+cart+adapt%2Celectronics%2C147&sr=1-4&ufe=app_do%3Aamzn1.fos.5137e923-c7be-4142-979c-7c68b6c26f63)

## iodd Mini USB 3.0 256-bit Secure encrypted SSD Drive
At the start of my career in IT, I distinctly remember maintaining a small zipped binder of USB drives, each 16 GB, each containing the bootable installation media for various operating systems used in my environment. It worked, but it certainly was not convenient and required a lot of upkeep as new media became available.

Some years ago, I picked up iodd's mini-USB SSD drive. This little device has an m.2 SSD inside, which is user-replaceable, and can hold a large quantity of ISOs and installation media. The firmware on the board allows you to mount those ISOs and present them to a physical system as a virtual CD-ROM drive. If you've worked with Dell iDrac or similar IPMI platforms and used the virtual media mapping functions in those systems, this is similar, but occurs on a physical level.

It weighs virtually nothing, slips into your pocket, and is simple to maintain. At just over $100 USD at the time of writing, I highly recommend having one of these around for desktop hardware technicians or small shops where time savings are crucial, and staffing levels are low. I especially recommend this for shops where an imaging/deployment tool is unavilable (SCCM or other PXE boot, SmartDeploy, etc.).

[Link](https://www.amazon.com/256-bit-Secure-encrypted-Drive-256GB/dp/B07Y465VX1/ref=sxts_rp_s_a_1_0?content-id=amzn1.sym.3432eb1a-1558-4445-9430-9bb3e7f7b9b7%3Aamzn1.sym.3432eb1a-1558-4445-9430-9bb3e7f7b9b7&crid=WP3874YV3ZNH&cv_ct_cx=iodd&keywords=iodd&pd_rd_i=B07Y465VX1&pd_rd_r=3beb27e0-ab5b-4250-bc41-92fc55d53cdf&pd_rd_w=2lydt&pd_rd_wg=aCQHI&pf_rd_p=3432eb1a-1558-4445-9430-9bb3e7f7b9b7&pf_rd_r=P4SD2MQPNHRNRB8F22EK&qid=1687409113&sprefix=io%2Caps%2C330&sr=1-1-5985efba-8948-4f09-9122-d605505c9d1e&ufe=app_do%3Aamzn1.fos.d977788f-1483-4f76-90a3-786e4cdc8f10)

## NetAlly LinkSprinter
NetAlly (also known as NetScout) makes a wide range of diagnostic network gear. I've had the pleasure of using their EtherScope nXG, their flagship product, but I'd like to instead include their LinkSprinter offering in my list of favorite hardware. 

This thing is small--like fit in your pocket small. This battery-operated tool lets you plug it into a data drop or switch port, and gather facts about that connection. It will check for physical link at layer 1, see if it gets DHCP, get information about the switch its connected to, check for internet connection, etc. If there is an internet connection, the report of this information gets emailed to you. Additionally, you can connect your smartphone or other WiFi-enabled device to it's ad-hoc network to view the report via a web browser. 

While handy for a systems administrator, it is **extremely valuable** to be able to hand one to a technician and have them use it as a diagnostic tool. At around $400 USD at the time of writing, this can be such a timesaver and huge value add, especially on mid-size teams.

[Link](https://www.amazon.com/NETSCOUT-LSPRNTR-300-LinkSprinter-Distance-Indication/dp/B00UD6G2OY/ref=sr_1_1?crid=2J55FNE5LR2QM&keywords=linksprinter&qid=1687409395&s=electronics&sprefix=linksprinte%2Celectronics%2C149&sr=1-1-catcorr&ufe=app_do%3Aamzn1.fos.5137e923-c7be-4142-979c-7c68b6c26f63)

## LTT Screwdriver
While a lot of people frowned on the price point of this screwdriver, and the fact that it's made by a "YouTube company," I have to say it's the single best ratcheting screwdriver I've ever used. It has quickly become a preferred and essential piece of my server room toolkit.

It's bit enough that you can put some force behind it, but small enough that it isn't clunky and unwieldy. Some bit storage, magnetized tips, and a fantastic and ultra-satisfying ratcheting mechanism make this a great piece of kit.

[Link](https://www.lttstore.com/products/screwdriver)

## LTT Backpack
Like the screwdriver, the backpack had some attention around it and many people voicing their concerns and outrage at the $250 USD price point. For years previously I had the [SwissGear Laptop Backpack for Tool Storage](https://www.amazon.com/SwissGear-Backpack-Storage-15-Inch-Notebook/dp/B07N141974/ref=sr_1_3?crid=2M7RU617IT0OI&keywords=swiss+laptop+tool+backpack&qid=1687409744&sprefix=swiss+laptop+tool+backpac%2Caps%2C156&sr=8-3&ufe=app_do%3Aamzn1.fos.d977788f-1483-4f76-90a3-786e4cdc8f10) and mostly liked it, but had some significant gripes such as the fact that it never sat upright correctly, the pockets were a little *too* specific, and it was *not* comfortable to haul around. 

I decided to bite the bullet after following the creation process of the LTT Backpack, and bought one. I've now had it for about six months, and I have absolutely zero regrets. The bag is very comfortable to wear for extended periods of time, even when loaded up a bit. The quality of the materials is excellent. It has tons of storage, with a nice balance of purpose-built pockets and large cavities for bulk storage. I would not hesitate to recommend this bag to anyone.

[Link](https://www.lttstore.com/products/backpack)

## StarTech 1P3FPC-USB-SERIAL Adapter
Have you ever had to fumble around with COM ports and drivers when you just need to console into a network switch? Because I have. And nearly every person I've worked with has. Don't bother!

One of my bosses recommended this to me after I'd expressed my woes of having to get my console cable to work every time I needed it. Since buying this one, I've never had a single problem. Plug it in and get configuring! It's the only adapter for console cables that I've not had issues with, and is only about $35 USD, so don't sleep on it, go for it.

[Link](https://www.amazon.com/StarTech-com-Retention-Converter-Prolific-1P3FPC-USB-SERIAL/dp/B09T75BYJP/ref=sr_1_9?crid=Q2ERMEYUX48&keywords=startech+usb+serial+cable&qid=1687411104&sprefix=startech+usb+serial+cabl%2Caps%2C163&sr=8-9)

# Conclusion
These have been just a few of my favorite tools, especially the ones that make my life as a systems administrator significantly easier. I hope some piece of the above information is helpful to you!