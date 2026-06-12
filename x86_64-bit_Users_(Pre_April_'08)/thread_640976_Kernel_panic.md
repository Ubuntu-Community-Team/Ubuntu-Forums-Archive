---
title: "Kernel panic"
date: 2007-12-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by bigdidz on 2007-12-14
[CENTER]:confused::confused:  Mayday!  :confused::confused:
[/CENTER]

I have a compaq R4000 laptop with Ubuntu 7.10 64-bit on it.  Today, I tried to accelerate the booting speed but now  it is taking close to infinity to boot.  Now, When I start up my computer, I have the fellowing errors:

[ 14.342175]  PCI: cannot allocate resource region 7 of bridge 0000:00:04.0
[ 14.342217]  PCI: cannot allocate resource region 8 of bridge 0000:00:04.0
[ 14.528820]  Kernel panic -not syncing: VFS: unable to mount root fs on unknown-bloc(0,0)

I looked on the forum but I found nothing.  Now, I am obligated to load from the Ubuntu-CD.  I look at my grub and it is looking okay.  I defenetly need help.

Thanks

Didier Amyot

---

### Post by bigdidz on 2007-12-16
HELP ME PLEASE!!!!

I looked on internet and I found no comprehensive information on how to solve my (huge) problem!!  My laptop is presently useless.  I can only use it by the Ubuntu CD.  I just want to be able to go on it!!!

Thanks

---

### Post by Thelasko on 2007-12-17
What did you do to "accelerate booting speed?"  Perhaps you should try to undo that first.  Did you try booting to recovery mode?

---

### Post by Thelasko on 2007-12-17
If all else fails and Ubuntu worked once before on your machine you can save your user data by saving your /home directory to other media, like a cd or external hard disk.  Then reinstall Ubuntu and move your files back to /home.  You will need to reinstall any programs that were not installed by default but your settings should still be there.

Sorry your problems is beyond my abilities to troubleshoot but this should get your machine up and running the quick and dirty way.

---

