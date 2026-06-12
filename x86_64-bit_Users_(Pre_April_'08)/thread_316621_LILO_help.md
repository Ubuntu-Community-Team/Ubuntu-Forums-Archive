---
title: "LILO help"
date: 2006-12-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by thebjoern on 2006-12-11
Hello again,

another newbie question:

I finally managed to get my x64 alternate install to work, but I still can't get to my windows. After GRUB didnt work, I finally got it running with LILO, but even though it said it detected windows, it doesnt give me a choice but boots straight to Ubunutu.

I got three HDs, one old IDE, one old SATA and a new 300 GB SATA, which is my /dev/sda On this the windows partition is /dev/sda1 and the ubuntu root partition is /dev/sda4

LILO said it saw a windows and suggested to be installed to the master boot record on /dev/sda1

How can I fix it to allow me to boot to windows again? Which files do I have to edit, and how? 

Thanks for your help,
Bjoern

---

### Post by odinfromvalhalla on 2006-12-11
you have to edit /etc/lilo.conf

check [this]("http://www.codecoffee.com/tipsforlinux/articles/6.html") for more help on getting lilo to boot windows

also a google search for "lilo.conf windows" will help

---

### Post by johatte on 2006-12-11
Try to find out from your bios in which order your motherboard reads your HD's. In my case bios reads ide disks first and after them sata disks. Try to install lilo in the MBR of your ide disk (propably hda).

---

