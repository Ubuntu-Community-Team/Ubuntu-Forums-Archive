---
title: "32 bit/64 bit dual boot?"
date: 2006-08-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kobussie on 2006-08-17
Hi everybody!
Yesterday I installed Ubuntu 5.10 - i386 version on my new AMD64 PC. Installation was the fastest Linux install so far - I tried a few distro's before. Everything works o.k. so far! :) 
About 3/4 of my 80 Gb HD is still empty, and I dont need Windows any more - I hope ;) .
Now I'm thinking of a dual boot system with also Ubuntu 6.06 in a 64 bit version, so that I can choose between 32 and 64 bit at boot time.
Anyone done this before, and does that work?

---

### Post by moma on 2006-08-17
I have installed several Linux-distros, both 32 and 64 bits in different partitions on the same machine (the machine is AMD Athlon 64,  3400+).  From the multi-boot menu I can choose Ubuntu 32bits, Ubuntu 64bits, Fedora 64bits etc  --- depending on what ever task/distro I need to test.

Notice that the latest installation will normally re-install the GRUB and replaces the menu.lst (/boot/grub/menu.lst) with its own.  **It is smart to have a backup-copy of the best menu.lst**. The machine generated menu.lst is rather unreadable if the menu list is long.

This is how I name the titles in menu.lst (kernel name, 32|64 bitch, which partition).

title          Ubuntu, kernel 2.6.15-21-k7,  32 bits on /dev/sdb2
...
title          Ubuntu, kernel 2.6.15-26-amd64-generic,  64 bits on /dev/sdb4
...
-------------------------

All distros (both 32 and 64 bits) can share the same **/swap** partition.

---

### Post by Kobussie on 2006-08-17
Thanks, I'll give it a try! (already ordered 64bit Ubuntu DVD)

---

