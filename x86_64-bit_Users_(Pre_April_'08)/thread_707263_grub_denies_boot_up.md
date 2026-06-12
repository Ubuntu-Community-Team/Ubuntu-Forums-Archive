---
title: "grub denies boot up"
date: 2008-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by QNo on 2008-02-25
Hi,

Kubuntu 7.10 on an AMD64 system.

System run for months. Last shutdown did not complete, i had to press the power button. Since that time, i can't boot anymore.

Grub is loaded. I find the correct menu entries. If i try to boot one, grub says it can't find the file.

I can edit the entries. Autocompletion works, the hard disk is found, all partitions are displayed. But no boot.

I tried to boot from CD. Everything ok, all drives detected. First, i tried to chroot into the installed system. Did not work, i think because of the CD system being x386 and the installet x86_64. So i copied /boot from installed to live system and tried to install grub again. Did not work, grub did not find the disk drive.

Any ideas how i can boot my system again?

---

### Post by Kilz on 2008-02-25
> **QNo said:**
> Hi,

Kubuntu 7.10 on an AMD64 system.

System run for months. Last shutdown did not complete, i had to press the power button. Since that time, i can't boot anymore.

Grub is loaded. I find the correct menu entries. If i try to boot one, grub says it can't find the file.

I can edit the entries. Autocompletion works, the hard disk is found, all partitions are displayed. But no boot.

I tried to boot from CD. Everything ok, all drives detected. First, i tried to chroot into the installed system. Did not work, i think because of the CD system being x386 and the installet x86_64. So i copied /boot from installed to live system and tried to install grub again. Did not work, grub did not find the disk drive.

Any ideas how i can boot my system again?

You can take a 64bit install cd and choose rescue a broken system to see if it can help you.

---

### Post by QNo on 2008-03-06
There is no such option on my 64bit install CD!?

---

