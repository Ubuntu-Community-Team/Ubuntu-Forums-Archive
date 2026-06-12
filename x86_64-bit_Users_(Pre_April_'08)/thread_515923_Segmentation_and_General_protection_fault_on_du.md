---
title: "Segmentation and General protection fault on du"
date: 2007-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by ggathrig on 2007-08-02
Last week I installed Ubuntu 7.04 desktop AMD64 on all new hardware including:

Intel Core 2 Quad Q6600 Kentsfield 2.4GHz 2 x 4MB L2 Cache LGA 775 Processor 
ASUS P5K LGA 775 Intel P35 ATX Intel Motherboard 
Seagate Barracuda 320GB 7200 RPM SATA 3.0Gb/s Hard Drive 
Mushkin 4GB(2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400)

Everything was working like a dream until this morning when I issued a 'du' command and got a segmentation fault.  I got the same thing issuing 'ls' on a particular directory.  Then I got a "kernal...general protection fault 0000 [15] SMP"  Then the system froze.  

After a reboot, everything (including those commands on those directories) is working fine. Nonetheless, I am a little disconcerted.  Any insight on what happened (or is happening)?  

Any help appreciated.

---

### Post by praxis22 on 2007-08-03
Hi,

Sounds dubious.

You might want to try recompiling your kernel, or reseating your RAM.

If you recompile your kernel remember to enable core 2 support, you can find out how to do this with the "master kernel thread" search for it.

---

### Post by ggathrig on 2007-08-03
Thanks for the response and the tips.  
GG

---

