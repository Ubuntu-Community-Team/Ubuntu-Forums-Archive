---
title: "Dual Boot with Two Hard Drives"
date: 2008-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by chrism66 on 2008-01-25
All right I am thinking about taking my Linux HD and put it in my XP x64 system. I would like to dual boot. What would be the easiest way to do this so that grub will see the xp hd? Linux HD is a 320gb Sata, XP x64 hd is a 120gb Sata.

---

### Post by logos34 on 2008-01-25
Plug in the drive, boot up and go into the bios and change the hard disk boot order so ubuntu/320 gb drive is first.  Boot ubuntu and add windows to [menu.lst]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk") and[ fstab]("https://help.ubuntu.com/community/MountingWindowsPartitions#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971").

Add windows line to /boot/grub/device.map:

(hd1) /dev/sdb

---

