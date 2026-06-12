---
title: "Nvidia driver with &gt;3GB Memory"
date: 2008-08-24
forum: x86 64-bit Users
---

### Post by gerrymeister on 2008-08-24
Hey Guys!

Last week I upgraded the memory of my machine running hardy from 2GB to 6GB. Somehow my nvidia-driver does not seem to like it and hangs at the moment I'm supposed to see the nvidia logo followed by the gnome login screen. When I go into recovery mode and change the driver to vesa or pull my nvidia-card out and use my onboard ati instead(using either vesa or the ati-driver), it boots just fine.

I've searched google for this problem and it seems that there are other people having the same problem as soon as they upgrade their memory to 4GB or more. I haven't found a solution yet, though. These are my specs:

64-bit Ubuntu Hardy
Motherboard: Asus M2A-VM
Processor: AMD Athlon 3800+
Memory: 6GB DDRII
Graphics: Nvidia Geforce 7900GS (onboard ATI X1250)

---

### Post by insane_alien on 2008-08-24
go into your bios and see if it has something called 'memory re-mapping' if it does enable it.

this has worked for me.

---

