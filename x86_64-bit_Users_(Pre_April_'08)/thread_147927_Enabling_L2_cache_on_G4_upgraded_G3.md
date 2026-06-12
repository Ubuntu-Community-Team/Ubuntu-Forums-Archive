---
title: "Enabling L2 cache on G4 upgraded G3"
date: 2006-03-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by smileyme on 2006-03-21
I installed a 466 MHz G4 into my AIO G3. It seems to be working ok, but I suspect the L2 cache isn't working. I tried to "Set Cache" in BootX, but its grayed out. What terminal command do I use to check it.

Rick :)

---

### Post by jdp on 2006-03-21
Did you use the script included with BootX, as described in the ReadMe?  Doing a quick [Google](http://www.google.com/search?&rls=en-us&q=bootx+set+g3+cache&ie=UTF-8&oe=UTF-8) turns up alot of info, but generally aimed at PCI PowerMacs with G3 upgrades.  I dunno if the G4 needs other special tweaks, and I dunno if the G3MTs I've worked on really turned the cahce on or not, as I didn't think to check for sure.

---

### Post by ssam on 2006-03-21
```
cat /proc/cpuinfo
```
should tell you all you need to know about your cpu.

---

### Post by smileyme on 2006-03-21
> should tell you all you need to know about your cpu.

Thank you for that. I'll try it and see what it turns up.

Rick :)

---

### Post by smileyme on 2006-03-22
> cat /proc/cpuinfo

This did show some useful info, but alas, no cache. I tried it on my PC, and it showed "Cache size: 256 KB". So I assume if the cashe were enabled on the Mac, it would also show cache size.

> Did you use the script included with BootX, as described in the ReadMe?

Unfortunately, the "GrabG3CasheSetting" is only for G3s. When I try to run it, it says "Error, CPU is not a G3". ](*,) 

Rick :)

---

