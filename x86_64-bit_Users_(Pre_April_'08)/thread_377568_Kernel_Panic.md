---
title: "Kernel Panic"
date: 2007-03-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by scuttle.VB on 2007-03-06
i have got ubuntu 6.10 running on an AMD dual core laptop.
everything was fine till yesterday.today when i tried to boot into linux i got the following message:
(IN RECOVERY MODE)
/lib/libc.so.6 not found   .....
attempted to kill init

any suggestions

---

### Post by kleeman on 2007-03-06
Sounds like your root partition is not being seen by the startup programs (init). Have you recently updated the system in particular the kernel? As a crosscheck that this is not a hardware issue try booting from the livecd.

---

### Post by scuttle.VB on 2007-03-06
i could boot from the live cd(6.06 though) easily.
i did install a program to access linux partitions through windows Ext2Ifs and later uninstalled it.could that be the problem.i checked the linux partition and the file mentioned is present there. :confused:

---

### Post by kleeman on 2007-03-06
If you are a linux newbie I would recommend reinstalling. If you have a lot of stuff on your home partition do the manual partition thing in the installer and leave /home untouched. 

Otherwise the problem is likely in the grub config file (/boot/grub/menu.lst). If you can get the root partition mounted with the livecd try looking for an old version (eg menu.lst~ or menu.lst.bak or something similar) and slot that into place instead of the new file.

---

