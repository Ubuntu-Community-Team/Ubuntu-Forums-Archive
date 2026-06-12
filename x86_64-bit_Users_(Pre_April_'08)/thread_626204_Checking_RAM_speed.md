---
title: "Checking RAM speed?"
date: 2007-11-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by NeilBlanchard on 2007-11-28
Greetings,

I recently upgraded from 2GB to 4GB of DDR400 (PC3200 - 4X 1GB) on my Athlon 64 X2 4200+, and I think I have *finally* gotten the BIOS (Gigabyte GA-K8N Pro SLi) settings to where they are all being recognized and running at DDR400 and their rated latency.  (And boy it was a bit of a struggle...)

It kept reverting to a 2/1.66 divider instead of 2/2, and I had to up the voltage to the RAM, the CPU and the Hypertransport by a little bit.  It is *like* I am overclocking, in a way, by having all that RAM in there -- I'd hate to try to get the thing to do the same with 4X 2GB, which it supposedly can do...

Is there an easy way to verify that the RAM is in fact running at DDR400, while booted in Ubuntu?

TIA, Neil

---

### Post by Rmantingh on 2008-01-15
The only program that I could find is lshw but there may be others.

$ sudo apt-get install lshw
$ lshw

Spool the output to a file and look for keyword "memory".
You should find some spped info below there.

Hope this helps.

---

### Post by NFITC1 on 2008-01-15
> **Rmantingh said:**
> The only program that I could find is lshw but there may be others.

$ sudo apt-get install lshw
$ lshw

Spool the output to a file and look for keyword "memory".
You should find some spped info below there.

Hope this helps.

You should also run lshw in super user mode. Otherwise it just tells you how large the total memory is. Super users get a lot more details.

---

### Post by Jouke74 on 2008-01-15
Easiest way is to run memtest86+, third option from your Grub menu. You might need to press escape to show this.

---

### Post by Yellow Pasque on 2008-01-16
Hi Neil. Just wanted to give you an SPCR shoutout (I'm known as 'jackylman' on there).

---

