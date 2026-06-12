---
title: "Can't install OS X!"
date: 2006-05-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by jnovek on 2006-05-21
I'm a long time Linux user, but a Mac n00b.  I got my hands on a 500 Mhz 15" TiBook, I want to dual boot Linux and OS X on it.  I've heard great things about Ubuntu (I really like it now that I've tried it, BTW) and I have run Debian in the past, so I thought I would give it a shot.

I formatted the hard drive and installed Ubuntu, disregarding the suggestions that docs gave to install OS X first.  Oops.  Now when I try to install OS X, I get to the point where it asks me what device I want to install on, and I've got nothing.  No hard drive.  Just a big empty selection screen.

I believe that my partitioning scheme is as follows (without looking, the laptop is all the way in the other room):
hda1: Some crazy 35k Apple something-or-other partiton
hda2:  yaboot partition (I think)
hda3: /boot
hda4: swap
hda5: /
hda6: Free space (why does fdisk call this hda6?)

Any ideas?  I've fiddled with fdisk a bit, very different from fdisk on my x86 systems.  I'm afraid to try anything in this fdisk w/o any guidance.  I haven't done much with this install, and I don't mind nuking and re-installing everything, OS X and Ubuntu.

Jaosn

---

### Post by EuroCity on 2006-05-21
The easiest thing would probably be to partition the drive from Disk Utility (on the OS X CD), with 2 HFS+ Journaled partitions, install OS X on the first one and then let the Ubuntu CD installer automatically partition the second one: for example, half of the space for OS X and half for Ubuntu.

---

### Post by jnovek on 2006-05-21
This may seem silly, but I'm not sure how to get into Disk Utility.  When I press "c" at the boot prompt, it goes right into OS X install; I am never prompted for any repair/restore utilities.

Jason

---

### Post by jnovek on 2006-05-21
I worked out how to open disk utility -- it is literally in the utilities menu on the OS X install program.  I added an HFS+ partition at the end of the disk, it's installing OS X now.  Will OS X hijack control of booting when it installs (I'm thinking of what Windows does on x86 if you install it after Linux)?  If so, how do I fix this?

Jason

---

### Post by EuroCity on 2006-05-22
So, if I understood correctly, you still have the original Ubuntu installation and added OS X at the end of the drive...?

Well, if it's so, you should edit your yaboot.conf file in Ubuntu (to include the new OS X partition) and then run sudo ybin -v to update the bootloader; you can google on how to do this...

Now, the problem is to get into Ubuntu, as OS X probably set itself as the startup disk: you could try to hold down the option key at startup and then select the disk with the little Linux badge on it, maybe, if it's still there (this would temporarily recreate the previous situation, without OS X installed).

If this doesn't work, you should try to rescue the system in some way: but I really don't remember how you do this with Ubuntu, so probably someone other could explain this better.

That's also why it's probably better to install OS X before Linux: that is, an HFS+ Journaled partition for OS X at the beginning of the drive and the remaining space for Ubuntu (you can even let Disk Utility leave this as unpartitioned, free space: even easier than making 2 HFS+ partitions and then erasing the second one within the Debian installer)...

---

### Post by Ptero-4 on 2006-05-23
OSX will overwrite the contents of the crapboot's partition. But since you reserved some free space for OSX and installed it in there. The ubuntu partition is still in it's place. You can use the "Option" bootloader to boot ubuntu and if you restore the crapboot bootloader, OSX will still be there b/c changing the bootloader doesn't delete or alter the partitions or partition table.

---

