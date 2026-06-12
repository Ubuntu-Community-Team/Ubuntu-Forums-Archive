---
title: "Dual Boot 64 and 32bit Hoary"
date: 2005-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by egghead3 on 2005-04-16
I just put together an athlon64 2800 system to run linux and have been running Ubuntu i386 for about a week and love it. I'd like to try the 64 bit version, but keep (or reinstall) the 32 bit version for the ease of installing things like multimedia codecs and generally not having to worry too much about whether packages and libraries are available. The only thing I would need 64 bit linux for at the moment is matlab and java development anyway. If I can successfully get a chroot 32 bit environment working in 64 bit Ubuntu, I might then move to 64bit full time, but Id like to keep the 32 bit system as my primary OS for the moment.

I was thinking of having a shared swap partition, a small partition (10, 20 gigs?) for each Ubuntu, and a larger partition for general storing of files. I have 1 160gb HD to work with.

Can I resize my current Ubuntu partition easily or is it better to do two completely fresh reinstalls? Will grub configure automatically when I install the second Ubuntu? I'm a bit of a newbie to linux so Id appreciate any specific directions anyone can give me to do this.

Thanks

---

### Post by wmcbrine on 2005-04-17
ext2resize. As with any such tool, use it at your own risk. But the description claims it's "quite safe these days".

---

### Post by egghead3 on 2005-04-17
Fortunately I have no essential data on the drive, so if anything goes wierd I can just do a reinstall. Its more for the convenience of not having to reinstall all the packages I installed.

---

