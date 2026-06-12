---
title: "Trouble with Compal FL90"
date: 2009-06-21
forum: x86 64-bit Users
---

### Post by ubunboy on 2009-06-21
Hello

I had some problems with a previous install of 9.04, ref [http://ubuntuforums.org/archive/index.php/t-1138213.html](http://ubuntuforums.org/archive/index.php/t-1138213.html). 

At that point I had overlapping partitions which I thought caused the error. Below is a print from the partitions I use now. As you can see there is no overlapping partitions now, but yesterday it happened again. This time it happened when I tried to log into the computer after a few hours. The screen was black and the only thing I could do was to move the mouse around. I had to use the power button to restart and then I got GRUB error 17. At the time I was using Transmission and Pidgin. Transmission was downloading to desktop. Is that a problem? I am also thinking that maybe the driver for my NVIDIA GeForce 8600M GT - 256 MB GDDR2 400MHz can cause the problem.

Anyone who has experienced the same? Will it help if I make a separate boot partition?

Thanks

[php]Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd04c0681

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        2687     2048287+  82  Linux swap / Solaris
/dev/sda3            2688        5237    20482875    b  W95 FAT32
/dev/sda4            5238       25634   163838902+   b  W95 FAT32[/php]

---

### Post by giorgio130 on 2009-06-27
maybe it's related to this bug:
[https://bugs.launchpad.net/bugs/346691](https://bugs.launchpad.net/bugs/346691)
quite frequent on compal laptops. you can either upgrade your kernel or enabling AHCI.
Further information are on launchpad related page.

---

