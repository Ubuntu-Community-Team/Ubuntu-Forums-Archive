---
title: "Problem with grub installing fakeraid in festy fawn"
date: 2007-06-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by fonsocm on 2007-06-15
Hi.

I have a computer with one intel core duo, intel board G965 and Vista installed in a fake RAID 0.

I want to install Feisty Fawn x86_64 in the raid, I am following the instructions in: [http://ubuntuforums.org/showthread.php?t=464758](http://ubuntuforums.org/showthread.php?t=464758) and the fakraid howto.

I followed the steps in the first post and it goes well until grub gives a fatal error. Then I try to follow the instructions in the post to install grub manually:

- chroot /target
- grub
-  device (hd0) /dev/mapper/isw_diagfejhc_Volume0 -> it's the name of the raid
- root (hd0,2) -> it's the / partition, I have / and /home
- setup (hd0)

And I'm obtaining an error: Error 17: Cannot mount selected partition. I tried:

find /boot/grub/stage1

I obtained Error 15: File not found

and 

grub-install  /dev/mapper/isw_diagfejhc_Volume0

I obtained /dev/mapper/isw_diagfejhc_Volume0 does not have any corresponding BIOS drive

Can someone help me with this problem? How can I make to install grub?

Thanks.

---

### Post by ©TriMoon® on 2007-06-15
You should put your "/boot" on a regular partition because grub, or anyother bootloader, dont know how to handle raid / lvm....
Also see my thread: [LVM and booting problem]("http://ubuntuforums.org/showthread.php?t=444332")

---

### Post by cowosnhigh@yahoo.com on 2007-07-14
Hi,

I am installing an almost identical setup, and I've run into the exact same problem. How did you fix this issue?


Thanks

---

### Post by Manganic on 2007-07-15
> **fonsocm said:**
> Hi.

I have a computer with one intel core duo, intel board G965 and Vista installed in a fake RAID 0.

I want to install Feisty Fawn x86_64 in the raid, I am following the instructions in: [http://ubuntuforums.org/showthread.php?t=464758](http://ubuntuforums.org/showthread.php?t=464758) and the fakraid howto.

I followed the steps in the first post and it goes well until grub gives a fatal error. Then I try to follow the instructions in the post to install grub manually:

- chroot /target
- grub
-  device (hd0) /dev/mapper/isw_diagfejhc_Volume0 -> it's the name of the raid
- root (hd0,2) -> it's the / partition, I have / and /home
- setup (hd0)

And I'm obtaining an error: Error 17: Cannot mount selected partition. I tried:

find /boot/grub/stage1

I obtained Error 15: File not found

and 

grub-install  /dev/mapper/isw_diagfejhc_Volume0

I obtained /dev/mapper/isw_diagfejhc_Volume0 does not have any corresponding BIOS drive

Can someone help me with this problem? How can I make to install grub?

Thanks.

Have you taken "savedefault" out of menu.lst?  Also make sure you take out the word "splash"

Check out FAKERAID:HOWTO for more detail.

---

### Post by fonsocm on 2007-07-16
My problem was caused by using the tool for admin disks in Vista to create the partitions. I erased the partitions and I created them with gparted like in the tutorial.

Actually, I have installed Ubuntu in the fakeraid and it works without problems. My only problem is with Kubuntu, it doesn't recognize the accents correctly.

---

