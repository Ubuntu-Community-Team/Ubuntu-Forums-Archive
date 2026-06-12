---
title: "Is it possible"
date: 2008-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by H_a_D_3_z on 2008-03-10
I am currently in transition from the VVindows to linux.  But my question is when i set up Ubuntu I apparently didn't make my partition big enough.  I have something like 3 Gigs for linux and 223 Gigs for vista didn't realize it.  I would like to make my partition bigger is it possible.  By the way i have a dual boot with vista.  thank you

---

### Post by MarocoKong on 2008-03-10
Well you could try resizing your harddrive with gparted (install it with packagemanager called "synaptic" if its not already on your system) - and by the way consider creating an own home partition... saves a lot of time on system upgrades, moves to other computers and so on... anyway...
regarding resizing with gparted.... I'm not sure all your data will survive though!! especially if your windows partition is ntfs-formatted... so if you have some external harddrive a backup would be strongly (!!!!!!!!) recommended ;-)

wish you luck ;-)

---

### Post by warp99 on 2008-03-10
You can resize the partition using a gparted LiveCD or LiveUSB:

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

This is the Gnome disk partitioner that allows numerous partition management features:

[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)

As an alternative you can boot to a Ubuntu LiveCD and also use gparted, but you would have to umount the drives before shrinking and/or growing any partitions. As always please backup your data before performing any partition operations. :)

---

### Post by tgalati4 on 2008-03-10
Perhaps give Linux 10 GB?  It is a full operating system.  It needs a little room to grow.

---

### Post by MarocoKong on 2008-03-11
"install using synaptic" to resize root while running?? *hand hits forehead* what am I writng? Sure you would need a livecd to resize your Linux-Root as you described... sorry  ;-) at least gparted was right ;-) did it work?

---

