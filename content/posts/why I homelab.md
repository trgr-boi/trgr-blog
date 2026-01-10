---
title: Why I Homelab
date: 2025-12-21
tags:
  - homelab
---
Hi,  
Trgr here!  

Today, I want to talk about why I homelab. It is a hobby that I, in very small amounts, started doing as a kid, but only last year started to explore deeper.

### Finding out about networks

I, as many people my age, played a lot of Minecraft as a kid (and still do). Me and my friends wanted to play together. We could do this via public servers and did this for a while. Playing everything from Hunger Games to Skyblock.  
We found out that we cloud turn on LAN when we were at each others home. This way we could play on out own worlds, not on someone else's server. But with the issue that we needed to be at each others home.  
We had no knowledge yet of what a **LAN** or **WAN** was. We just knew that the _'L'_ in _LAN_ stood for _'local'_.  

Around this time, one of my friends informed me about *Teamspeak*. He had joined some public servers, and after doing some research, we found that one of us could host our own server on a computer. All we needed was that person's _'IP'_, whatever that was. Some sort of name for your computer. It worked flawlessly when we were at his house!  
When we got home, we got the exact same issue as we had with the *Minecraft* LAN. Whilst his IP stayed the same, we could not connect to it.  
After doing some research, we found a tool called '*Hamachi*'. Now I know that it is a VPN that puts everyone that joined in the same virual network, but back then, all we knew is that we could join this and everyone could use the "host" his IP and join. As if we were in the same house. Quickly after that, I setup my fist Minecraft server so anyone on the VPN could join whenever without the need of the person who had the savefile to start the LAN. I just knew if I kept my pc turned on, anyone could join.  

We had no deeper understanding on how all of this worked, only that we had to do these steps to make it work. We used this process for multiple games like *Garry's Mod, Terraria*,...

This was all I knew for a while.  
Eventually (and in a nostalgic way, sadly) we moved on to Discord, so no need for *Hamachi* there, and more and more games started to have their own game servers. Or at least easy ways to host a private game on their servers. So I didn't really have a need anymore to learn about this process...

### Becoming a fascination

Fast-forward to Oktober 2024.  
I started *Applied Computer Science* at *HoGent*. I started to learn more about what Linux is, I used it when I was younger but I didn't really understand what is was and how it worked, and became more and more interested in "data sovereignty". I wanted to be less reliant on services of big tech. I had become more and more interested in open-source these last couple of years, but now I finally started to see the real strength and scale of what this actually was. I wanted to have everything of my data locally. Not using Google Drive or *iCloud* anymore. But this comes with some issues;

- Devices don't come with a lot of storage anymore. I bought a *m1 Macbook* Air with only 265GB of storage, which quickly fill up. This in combination with wanting to have everything locally was a disaster.
- I wanted to have those files on all of my devices just like when I used Google Drive or *iCloud*.

First I used *Github* to sync files from my *Macbook* to my pc, but you could feel that it was not meant to sync an entire documents directory. So quickly I found *Syncthing*. It felt magical. It just worked, exactly like *iCloud*, but with one issue; both devices had to be on. If I did some stuff on my Mac whilst my phone was not on the same network and turned my Mac off, I coudn't get those files on my phone. This led me to a central server. A computer, just like the *Minecraft* server, that stayed on always. All my devices pushed and pulled changes from the server. It felt powerfull. This made the snowball roll.

I could only work on my server when I was home, but *Syncthing* has a feature where devices can still sync, even when on a different network. But then I found out about VPN, and learned that Hamachi was doing the same. But I saw everyone using Tailscale, instead of Hamachi, so I did the same. Then I learned about ports, docker, cloudflaretunnel, reverse proxy,...  
Every month, I learned a lot of new stuff about it, both at school and in my own research. This happened at the same time as my political views on the big tech companies and privacy started to form, pushing me to try to do more on my own. To stop relying on other services and take that power in my own hands.  
Did I have data-loss-scares, yes. But did that lead to a better understanding on how to store and manage data, also yes.  

My setup now is ever-changing, but I feel it more and more shaping to a organized and stable. With a old laptop as main server, a Raspberry Pi as experimental server and my pc as (a shitty) LLM server, I feel that I can do so much already. Homelabbing always seemed like a very expensive hobby, but whilst it has cost me some money, most of it I could do with tools that I already had or were free.  
Learning about the terminal and ssh made it so that I stopped seeing machines as e.g. 'laptop', but as a computing devices that I could access from anywhere as long as I had a connection. And now that I am learning about *Ansible*, those separate devices are become more and more like one big system that can be setup in a declarative way, where even if I lose my server configuration (not talking about data like music or files), I can easily set it up again by changing IP addresses in a yml file and running a Ansible-playbook (this is still a work in progress though). Making it much less scary to do these things myself.  

In the next couple of posts, I will start to explain how my homelab currently looks and works, how I am transitioning from doing everything manually to switching to Ansible, what my near-future plans are to improve this, and how I want to start to help the people around me by offering non-essential services that I host myself.  

Hope that you enjoyed this.

See you soon,  
Trgr
