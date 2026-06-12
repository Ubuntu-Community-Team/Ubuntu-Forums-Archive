---
title: "Custom Kernel Testing required! - 64bit only!"
date: 2008-06-28
forum: x86 64-bit Users
---

### Post by db260179 on 2008-06-28
Hi People,

I've heard alot of people complain about the current kernel (2.6.24.19) crashing machines, slowing down. I too have experienced these issues on several pc's of my own.

You can try my custom ubuntu kernels. Amd64 only and generic (intel etc)

64bit kernels only.

[kernelamd64.rar]("http://gallery.mulberry.towerhamlets.sch.uk/kernelamd64.rar")

[kernelgeneric.rar]("http://gallery.mulberry.towerhamlets.sch.uk/kernelgeneric.rar")

To Install, Download either kernelamd64.rar if you processor is AMD64

or if not, download the kernelgeneric.rar (intel dual core 2, etc)

Extract to your home folder, (rar e kernelgeneric.rar ~/)

Install via gui or command line - (dpkg -i )

What i've done with these kernels, is as follows:

* Change the scheduler from SLUB to SLAB (SLAB works well for me)

* Increase from 250hz to 300hz

I'm really interested to see if changing these two settings makes a difference to your setup? - changing the scheduler is suppose to help with the suspend/resume with ati cards.

I own a nvidia card, and dont experience any crashing with these two settings.

If this works out for a lot of people, i think we should feed this back to the devs, to get the default kernel changed in a ubuntu!

Thanks
David :guitar:

---

### Post by XAVeRY on 2008-06-28
As far as I know, the original Ubuntu kernel is tickless, so the frequency chosen in the config doesn't matter.

Besides, why did you change the frequency? How should users benefit from this?

---

### Post by db260179 on 2008-06-29
Doh!, you are right!

SLUB to SLAB, does make a difference in reference to the stability side.

> **XAVeRY said:**
> As far as I know, the original Ubuntu kernel is tickless, so the frequency chosen in the config doesn't matter.

Besides, why did you change the frequency? How should users benefit from this?

---

