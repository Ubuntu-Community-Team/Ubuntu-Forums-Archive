---
title: "Removing Boot Manager"
date: 2006-03-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by ToBeHuman on 2006-03-26
Hello,

I was trying to install Ubuntu on my Rev. B 17" iMac G5 and couldn't get it to work successfully. I would now like to remove Ubuntu. I know how to delete the Ubuntu partition in OS X's Disk Utility, but how to I get rid of the boot manager? I know on Windows machines the command is  "fdisk /mbr". What is the equivalent of that command on Macintosh? Thanks.

---

### Post by aimislame15 on 2006-03-26
You remove it the same way you removed the ubuntu partition... it shows up in disk utility... just reformat it as free space.

---

### Post by ToBeHuman on 2006-03-26
I don't see any partitions for the boot manager. Isn't the boot manager on the disk's MBR? Is there any way to tell OS X to rewrite the disk's MBR with whatever it, OS X, puts there by default?

---

### Post by Rob Friefeld on 2006-03-26
I hvae seen it mentioned that if you set the start up disk (System Preferences->Startup Disk) on the Mac it will overwrite the boot manager. Wouldn't hurt to try it.

---

### Post by jdp on 2006-03-26
There is a small HFS partition that holds the boot info for YaBoot.  It might not show up in Disk Utility.  You can boot the install CD for Ubuntu, and use the **parted** command to remove the unwanted partitions (don't take out any of the first 3-4, as those are probably patch partitions).  You then might be able to use parted to resize the MacOS install to fill the newly empty space.  You'd want to follow many of the setps [on the HFS+ resize HOW-TO](http://www.ubuntuforums.org/showthread.php?t=89960) except you want to grow the HFS, instead of shrink it.

I've only used parteed to shrink an HFS partition, I've never used parted to increase the size of an HFS partition so I have no real idea how safe it is.  Be wary and have backups of your stuff, just in case.

---

### Post by MonolithTMA on 2006-03-27
[QUOTE=Rob Friefeld]I hvae seen it mentioned that if you set the start up disk (System Preferences->Startup Disk) on the Mac it will overwrite the boot manager. Wouldn't hurt to try it.[/QUOTE]

That does do it. 
I did it accidentally with Startup Disk.

---

### Post by ToBeHuman on 2006-03-27
Thanks for all the info. The System Preferences >> Startup Disk overwrote the boot manager and everything is back to how it was before I installed Ubuntu.

---

### Post by jdp on 2006-03-27
As a fair warning: The boot manager is still there, it's just that the computer is not using it to boot.  Unless you already repartitioned the space you had for Ubuntu, then you've still got un-reclaimed drive space sitting around useless until you go in a fix it.  If you aren't worried about it, that's ok.  I just want to tell you that it's "still there" even if the computer isn't using it.

---

