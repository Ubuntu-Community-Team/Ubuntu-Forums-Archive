---
title: "Difference in x64 Linux OS?"
date: 2009-10-17
forum: x86 64-bit Users
---

### Post by rob22941 on 2009-10-17
I'm curious, are there differences or advantages in different linux distros for a x64 system? Like Opera, Ubuntu, Gnome, other recommendations? I have Ubuntu 9.04 on my 32 bit laptop I have NO complaints other than finding a efficient ipod compatible progtam. I'd like to put Linux on my desktop which is a smidgen faster. Are there any advantates or disadvantages over different linux versions for a x64 system?

:popcorn:

---

### Post by NoaHall on 2009-10-17
Flash will work better, although some people complain about it.

It will be to * in theory* process twice as much bits in the same number of time. But most apps don't use/need these bits.

---

### Post by QIII on 2009-10-17
You are limited to the amount of memory that can be addressed by a 32 bit system.

Unless PAE (Physical Address Extension) is enabled, you will be limited to 4GB -- or somewhat less in practice.

64 bit systems can address 16 EB of memory, which is a fantastically huge number.

64 bit systems are substantially more efficient in terms of processing, but you might not notice it unless you are doing some serious number crunching.

The big considerations here are memory and the path that the industry is taking.  While distros like Ubuntu will continue to support 32 bit systems well into the future, the world is going 64 bit.

---

### Post by linux4life88 on 2009-10-17
> **QIII said:**
> Unless PAE (Physical Address Extension) is enabled, you will be limited to 4GB -- or somewhat less in practice.

This is the biggest reason to use 64 bit is if you have 4gb or more of ram. For example my laptop has 4gb of ram but shipped with 32bit Vista, so on 3.3gb is recognized. Although, when I put Linux on I use 64bit and the whole 4gb was now being utilized. Basically you are wasting ram by using 32 bit.

---

### Post by rob22941 on 2009-10-17
Well what I have is a x64, 4gb of ram. So I guess that would work great. Only think preventing me from installing Ubuntu is finding a efficient program for my ipod...

---

### Post by linux4life88 on 2009-10-17
> **rob22941 said:**
> Well what I have is a x64, 4gb of ram. So I guess that would work great. Only think preventing me from installing Ubuntu is finding a efficient program for my ipod...

I don't know if this will help but here is an article form the Ubuntu Wiki

[https://help.ubuntu.com/community/PortableDevices/iPod](https://help.ubuntu.com/community/PortableDevices/iPod)

Hope this will help out.

---

### Post by falconindy on 2009-10-17
> **rob22941 said:**
> Well what I have is a x64, 4gb of ram. So I guess that would work great. Only think preventing me from installing Ubuntu is finding a efficient program for my ipod...
I'm using gtkpod-aac package for my 30gb ipod video. Works great.

---

### Post by rob22941 on 2009-10-17
Linux4life, that link was extremely helpful thanks alot.

---

### Post by linux4life88 on 2009-10-17
> **rob22941 said:**
> Linux4life, that link was extremely helpful thanks alot.

If you like Amarok or would like to try it this link might also help:

[http://amarok.kde.org/wiki/Media_Device:IPod](http://amarok.kde.org/wiki/Media_Device:IPod)

It actually lists out which Ipod devices Amarok works with, both fully, partially and not at all. I also tried to find a wiki page for Banshee but their wiki pages are down for maintenance right now. Glad I could help.

---

