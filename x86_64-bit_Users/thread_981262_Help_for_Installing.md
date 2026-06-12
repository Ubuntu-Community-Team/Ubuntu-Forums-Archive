---
title: "Help for Installing"
date: 2008-11-13
forum: x86 64-bit Users
---

### Post by Trancegonadz on 2008-11-13
I have a 64 Bit AMD Athlon Duo core HP brand PC.
Last night I spend 2 hours trying to instal 7.04 and after the installer did its work I rest my computer. When Ubuntu was loading it got stuck saying "GRUB error 20". Then today I made a new boot disk and tryed loading Ubuntu version 8 and this time when Ubuntu was loading I got "GRUB error 2". I tryed installing and deleting each instal disk 3 times and I kept getting the same error dispit choosing other options. Does any one have any idea what Error 2 or 20 mean? OR, does anyone have any ideas on how to fix this issue???

Any input is greatly appriciated!

Thank you,
Brad

---

### Post by toolfan2k4 on 2008-11-13
Try entering BIOS and resetting BIOS to failsafe defaults. Also make sure that all your hard drives are showing up in BIOS. That usually does the trick for me.

---

### Post by Sef on 2008-11-15
> Does any one have any idea what Error 2 or 20 mean?

GRUB error #2:

> 2 : Bad file or directory typeThis error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO.       

GRUB error #20:

> Multiboot kernel must be loaded before modulesThis error is returned if the module load command is used before loading a Multiboot kernel. It only makes sense in this case anyway, as GRUB has no idea how to communicate the presence of such modules to a non-Multiboot-aware kernel.       

---

