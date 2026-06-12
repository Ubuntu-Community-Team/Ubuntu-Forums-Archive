---
title: "boot error : PXE-EC8"
date: 2009-11-16
forum: x86 64-bit Users
---

### Post by kaito_kid on 2009-11-16
I've installed ubuntu 9.10 (64 bit) 2 weeks ago in dual boot with winVista (in the same partition, with wubi)
And yesterday, when booting, i've got this message :
> PXE-EC8 : !PXE structure was not found in UNDI driver code segment.
PXE-M0F : Exiting PXE ROM.
Operating system not found
Is there's a way to repair the system without having to reinstall ubuntu?

thx for your help ^_^

---

### Post by PRC09 on 2009-11-16
The only time I have seen this error is when my machine didnt see any of my drives on start-up and tried to boot from my network card.Try powering down remove the power source (power cable,battery if laptop)plug it back in and try restarting again....

---

### Post by sanderj on 2009-11-16
PXE is booting over your network (see [http://en.wikipedia.org/wiki/Preboot_Execution_Environment](http://en.wikipedia.org/wiki/Preboot_Execution_Environment)).

The fact that your system only tries PXE, and then quits, makes me think your system does not see your harddisk anymore, or does not see a bootloader on your disk.

First check: while booting, go into the BIOS, and check whether your BIOS does see your harddisk(s) at all.

Report back here.

---

### Post by kaito_kid on 2009-11-16
I don't think the problem comes from the hdd, because windows start normally.
also, i don't think the problem comes from the bios because if i copy somewhere else "root.disk" and "swap.disk" (in windows), and i reinstall ubuntu 9.10, it work. but if i replace the new "root.disk" and "swap.disk" with the old one of the ubuntu i was using, and then i restart my computer, i got the same error..... so i think the problem comes from the *.disk files (perhaps the files are corrupted, but why? i don't know and i hope not >_<)

---

### Post by PRC09 on 2009-11-16
I dont know if I missed something but at what point do you get the error message about the PXE?Is it the first thing that comes up when you boot or is it after grub loads and you select which os to boot into..

---

### Post by kaito_kid on 2009-11-16
first i see the toshiba screen (where i can access the bios if i want)
then it ask me to choose wich os i want
i choose ubuntu
then normally, it ask me to choose wich kernel i want
but before that, i see this error >_<

---

### Post by PRC09 on 2009-11-16
Okay,the error at that point would probably indicate that the bootloader doesnt see the disk drive Or that partition in wubi.I dont use wubi so I am just guessing on that.I would suspect that it is corrupted.I would also suspect if you are moving files in the ubuntu install(if possible?) around with windows then anything could happen.

---

### Post by kaito_kid on 2009-11-16
> **PRC09 said:**
> Okay,the error at that point would probably indicate that the bootloader doesnt see the disk drive Or that partition in wubi.I dont use wubi so I am just guessing on that.I would suspect that it is corrupted.


i tried to reinstall, everything ok, but if replace the files with the one wich didn't work, the error re appear. does that mean that the files are corrupted?

but what made this file being corrupted?
in windows, none of my files have never been corrupted....

---

### Post by PRC09 on 2009-11-16
Sorry,I am out of my league on this one,maybe someone else help from here...

---

### Post by kaito_kid on 2009-11-17
yeah.... maybe.......

---

