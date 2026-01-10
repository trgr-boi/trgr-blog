---
title: My Current Homelab
date: 2025-12-28
tags:
  - homelab
---

# My Current Homelab

In this post, I will go over how my homelab currently looks and how I got here in short.  
I am currently making a full ansible automation to remake my entire homelab. The services will stay the same, but I will change how it is maintained and on what it runs. More on this later. I see this as a sort of archive how it was. Something I can use to compare the new setup to.  

I will go into depth about:
- my devices
- operating systems
- services
- network

Hopefully this will give a good understanding on how I run things now.

# My Devices

My current devices are:
- `Lenovo Thinkpad L380 Yoga` (server)
- `Raspberry Pi 4` (testing server)
- `Lenovo Thinkpad L390 Yoga` ("work" laptop)
- `Macbook Air M1` ("personal" laptop)
- `custom gaming pc` (for gaming, duh) (also hosts llm)
- `iPhone XS` (main phone)

## Thinkpad L380 server

I started with my old laptop. A `Lenovo Thinkpad L380 Yoga`. I tried using this one as a Linux desktop, before I really understood Linux. I liked it, but comming from a M1 Macbook Air, the 720p display really made everything feel really small. I wass still uding a full desktop environment on it, which was wasting a lot of needed space on the screen. Leading to me always using my Macbook and the Thinkpad collecting dust.  
Then one day, I decided to just install `Fedora Server` on there. I didn't really understand yet what a server really was and how much it could do. But slowly it started growing. I quickly learned how docker makes it really easy to test new services, and organize ones I want to keep using. After I learned how `docker compose` worked at school, I transisioned all the containers I ran with `docerk run` to a compose file, which started my path towards automation.  

The great thing about this setup is that the host's OS does not matter. I can use all my services in a simple browser. I tried to find good client applications on my Macbook, but quicly started seeing the strength of just using the web ui. No different apps on different platforms.  
This wasn't an issue when I was just using a Macbook and iPhone. MacOS being Unix-based made this actually a much more enjoyable experience than using Windows (in my oppinion). And MacOS has great FOSS clients to use with most of my services. But when I started to add more and more devices with differen OS's, it became annoying to learn different clients for the same service. So I just started utilizing the web ui versions more and more. Only choosing for a client application when I would need it offline. (e.g. immich so I can see thumbnails & metadata even offline; Amperfy so I can download my music hosted on Navidrome;...)

The L390, which I call `thinkpad-server` (I know, very creative), is used as a combined storage server, and to host my services. I will go into depth into this in [services]. It had a 1TB external SSD for storage. I know storage over USB is not so safe, do I take weekly cold backups on a 2TB HDD. This is also a process I want to automate, but hopefully I have a dedicated storage server in the near future with redundant storage.

## Raspberry Pi 4

Tbh, not a whole lot is running on this. I even regurarly turn this one off...  
It only had a Grafana & Prometheus stack running on there. But this was mainly to learn the basics of Ansible. I will encorperate it more in the future. Maybe in my homelab, or maybe as a more protable mini server.

## Thinkpad L390

This is my Linux desktop. I daily drive Fedora i3 spin on here. After falling in love with i3, it's hard to go back so anything with a GUI. Whilst my Macbook is a lot better and faster at everything, it jsut feels slow because of MacOS...  
This laptop is mainly for "focussed" work. I didn't install any games on here. The only entertainment I really use on this is music, but often used together with "work".  
This is what I use for school, and everything to do with administration.

## Custom Gaming Pc

Don't expect to much from this one. It had a Ryzen 5 2600x, 16GB ram, and only a Nvidea GTX 1050 that I am borrowing from my girlfriend. I sold my GTX 1660 super because I was really addicted to gaming and wanted to stop. Now I don't have an issue anymore but no money to buy a better GPU.

I have tried running some llm models on here, and whilst not good, it works somewhat if I give it web search. The llm is running in Ollama and the webui is `Open WebUI`. But this is not used very often. It is just so behind the commercial llms that it makes it difficult to preffer it... It is just cool that I CAN run something like this myself

## Others

The rest is not really worth to talk about. It is just a macbook and an iPhone. Used to view the webUI of the services.

Everything is connected with a `TP-Link TL-SG108G` switch.

# Operating Systems

# Services

# Network