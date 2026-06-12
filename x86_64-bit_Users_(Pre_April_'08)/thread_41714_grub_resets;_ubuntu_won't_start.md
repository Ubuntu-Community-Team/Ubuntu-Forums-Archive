---
title: "grub resets; ubuntu won't start"
date: 2005-06-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by caminoix on 2005-06-14
hello :)

i've just installed ubuntu and have the following problem:

after reboot, the grub menu shows up but when i choose to run ubuntu, it shows something too fast to read it and then grub menu shows up again, this time in text mode.

what should i do?

---

### Post by caminoix on 2005-06-15
i've also tried booting it manually from grub's command mode with the following commands:

kernel (hd1,2)/boot/vmlinuz
initrd (kd1,2)/boot/initrd.img
boot

and it ends with saying:

Unable to load NLS charset cp437
NTFS volume version 3.1.
pivot_root: No such file or directory
/sbin/init: 428: cannot open dev/console: No such file
Kernel panic - not syncing: Attempted to kill init!

---

### Post by Alexander Kirillov on 2005-06-15
[QUOTE=caminoix]i've also tried booting it manually from grub's command mode with the following commands:

kernel (hd1,2)/boot/vmlinuz
initrd (kd1,2)/boot/initrd.img
boot

and it ends with saying:

Unable to load NLS charset cp437
NTFS volume version 3.1.
pivot_root: No such file or directory
/sbin/init: 428: cannot open dev/console: No such file
Kernel panic - not syncing: Attempted to kill init![/QUOTE]
 You sure that (hd1,2) is the correct disk/partition? This refers to second hard drive, not the first one: in GRUB, they start counting with zero: 
[http://www.gnu.org/software/grub/manual/html_node/Naming-convention.html#Naming%20convention](http://www.gnu.org/software/grub/manual/html_node/Naming-convention.html#Naming%20convention)

---

### Post by caminoix on 2005-06-15
i know that. in my other linux this partition is called sdb3, so in grub's terms it'll be hd1,2, or won't it?
i have sdb1 for currently mepis, sdb2 for swap and sdb3 for ubuntu, all primary. sda is for win until i get my wife to love linux truly ;)

---

