---
title: "[SOLVED] How to make Windows boot first using Grub in openSUSE 11.0 ?"
date: 2008-10-26
forum: openSUSE and SUSE Linux Enterprise
---

### Post by silvestros on 2008-10-26
Hi,
I have Windows XP and openSUSE 11.0 in dual boot. I want windows to be highlighted in the Grub menu instead of the openSUSE, when I turn on my laptop or make a restart. What do I have to do? 
Thanks.

---

### Post by silvestros on 2008-10-26
I forgot to tell you that I'm using KDE 4 (the version from openSUSE 11.0 without any updates). By the way, can you also tell me hoe to update the KDE 4?
Thanks again.

---

### Post by bwhite82 on 2008-10-26
As far as changing the boot order, simply edit /boot/grub/menu.lst

Make sure you have root privileges then:

> gedit /etc/boot/grub/menu.lst 

Find the entries near the bottom, they will look similar to this:
> 
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

> 
title		OpenSuse, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=590668a8-6701-45b2-b921-52229b0e6b17 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

Simply change the position of these entries in the file. You want the Windows entry to be above the others.

---

### Post by silvestros on 2008-10-26
Thanks Soldierboy, that really helped me.

---

