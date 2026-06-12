---
title: "Unable to mount Hard drives"
date: 2008-06-28
forum: x86 64-bit Users
---

### Post by marduk418 on 2008-06-28
Hey there, i have posted this problem on another thread, so i thought it would be ok if I make a single Thread about this.

The original Thread is here [http://ubuntuforums.org/showthread.php?t=843618]("http://ubuntuforums.org/showthread.php?t=843618")

I installed Ubuntu 8.04 without any problems, but as soon as i wanted to mount my hard drives, an error message pops up telling me that the drive could not be mounted.

My comp spec is as following:

Intel Core 2 Duo E4500 Processor
Motherboard ASUS P5B
XFX Nvidia GeForce 9600GT 512Mb GDDR3
2x Kingston 1GB DDR2 RAM
Maxtor 160Gb SATA2 (partitioned)
Seagate 250Gb SATA2


I appreciate your help in advance

---

### Post by kuja on 2008-06-29
You'll have to do what it says. You either have to mount that partition with the "force" option (at your own risk), or boot into windows, let it mount it, then shutdown cleanly. If you intend to use ntfs-3g in linux for mounting NTFS files, make it a point to "safely remove" if it's an external device, or to shutdown cleanly if at all possible :)

---

