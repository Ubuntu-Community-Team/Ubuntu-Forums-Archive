---
title: "[SOLVED] Issues performing a fresh install."
date: 2008-05-19
forum: x86 64-bit Users
---

### Post by O3CAndrew on 2008-05-19
Alright so I've been trying for the last hour to boot into my Live CD to give 8.04 a spin before I install it on one of my empty HDDs. Only thing is I get to the loading bar and about 1 second into the loading my computer reboots.

I've tried doing the following, which was suggested on another board via some Googleing:

pci=nomsi all_generic_ide floppy=off irqpoll

Here is my system specs:

- AMD Athlon 6400+ X2 @ 2.61GHz
- ASUS M2N-SLi Deluxe
- eVGA 8800GTS 320Mb
- Corsair XMS 4Gb Dual Channel PC 6400 4-4-4-12
- Western Digital 320Gb SATA-II (Dedicated to Ubuntu when I get it working)
- Western Digital 320Gb SATA-II (Windows Vista Home Premium 64bit)
- SATA-II DVD Optical

I burned the .iso file onto a blank DVD(+/-)RW disc and ran the md5 checksum and the disk checked out perfectly fine.

Any ideas as to what is causing this problem? I'm getting ready to just use the 32bit version as thats what I ended up doing for 7.10... But I would really like to have my 64bit installed.

Thanks for your help in advance :)

---

### Post by Kilz on 2008-05-19
> **O3CAndrew said:**
> Alright so I've been trying for the last hour to boot into my Live CD to give 8.04 a spin before I install it on one of my empty HDDs. Only thing is I get to the loading bar and about 1 second into the loading my computer reboots.

I've tried doing the following, which was suggested on another board via some Googleing:

pci=nomsi all_generic_ide floppy=off irqpoll

Here is my system specs:

- AMD Athlon 6400+ X2 @ 2.61GHz
- ASUS M2N-SLi Deluxe
- eVGA 8800GTS 320Mb
- Corsair XMS 4Gb Dual Channel PC 6400 4-4-4-12
- Western Digital 320Gb SATA-II (Dedicated to Ubuntu when I get it working)
- Western Digital 320Gb SATA-II (Windows Vista Home Premium 64bit)
- SATA-II DVD Optical

I burned the .iso file onto a blank DVD(+/-)RW disc and ran the md5 checksum and the disk checked out perfectly fine.

Any ideas as to what is causing this problem? I'm getting ready to just use the 32bit version as thats what I ended up doing for 7.10... But I would really like to have my 64bit installed.

Thanks for your help in advance :)

For the AMD64 version the alternate install cd is always better than the live cd.

---

### Post by O3CAndrew on 2008-05-19
Alright, I'll try downloading and burning the alternate CD. If it works I'll be posting back here from inside Ubuntu :)

---

### Post by O3CAndrew on 2008-05-19
Successfully installed 64bit using the Alternate CD :) Thanks man :D

---

