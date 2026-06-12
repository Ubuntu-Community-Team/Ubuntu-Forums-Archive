---
title: "I messed up firefox by installing a chroot."
date: 2006-05-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Yaks Hairbrush on 2006-05-17
So, I decided I wanted to install some 32-bit apps like WINE and DosEmu and Firefox with plugins. I followed the direction on "http://www.ubuntuforums.org/showthread.php?t=24575" to the letter.

The good news: 32-bit firefox works fine and has flash installed

The bad news: 64-bit firefox gives me a segmentation fault when I run it, usually after viewing 2-4 pages.

Appreciate your help
--Yaks Hairbrush

---

### Post by Yaks Hairbrush on 2006-05-18
I tried to fix the problem by removing the symbolic links, the /chroot directory, the new entries in the fstab file and the dchroot and debootstrap packages. In short, I tried to reverse all the changes made to the system by the addition of the chroot.

I then tried to re-install firefox using synaptic.

Unfortunately, 64-bit firefox still gives me segmentation faults.

](*,)

Any other ideas? I'd really appreciate them.

---

