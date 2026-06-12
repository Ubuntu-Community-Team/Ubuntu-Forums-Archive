---
title: "Dualboot Vista"
date: 2007-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by eyelessfade on 2007-10-26
So I find myself with both 64bit ubuntu and 64-bit Vista. I use AHCI which works great in both.

Exept: Grub won't boot Vista.

from grub:

title           Windows Vista
root            (hd0,0)
savedefault
makeactive
chainloader     +1


The only thing it does is reboot the computer.

ubunty live on hd1,0 and is happy.

Anyone?

---

### Post by dabl on 2007-10-26
Just a guess, as I don't run Vista.  But doesn't Vista make itself a small recovery partition, and then install the main OS on the second partition?  If that is true, maybe you should try (hd0,1) for the Vista boot partition.  :)

---

### Post by eyelessfade on 2007-10-28
Nah didn't work. only have two partitions on that disk. one for windows and one for something else.
I think the clue  is AHCI, perhaps together with my motherboard. Abit AB9 Pro.

I've found a workaround . Not the best, but better then nothing. I let windows bootloader load grub. And that way I get into linux. Windows I only use >1% of my computertime anyway.

---

### Post by mk4 on 2007-10-30
Here is my (slightly different) experience with dual boot:

Bought new PC HP AMD 64 x2 5000 with Vista (32-bit I guess) installed (like I had a choice), 2 disk partitions (~460 GB and ~20-40 GB HP recovery partition).

In Vista (Disk Management), I shrank the main partition (it allowed me to shrink down to ~220GB).

Rebooted from CD with Ubuntu Gutsy 64-bit desktop.

Started Install and created several partitions (/, /home, /data etc.) from unallocated space (~240GB). Completed Ubuntu installation.

On startup I have a choice to start Ubuntu or Vista (I don't know if it's Grub, but it's definitely Ubuntu loader).

I can boot both Ubuntu and Vista, no problems. It's funny noticing performance/responsiveness and memory usage between the two OSs :)

---

### Post by Eriol_Ancalagon on 2007-10-30
I dunno man, as I'm running gutsy x64 and vista x64 with no bootloader issues, so I can only wish you good luck in resolving your problems.

---

### Post by Nebvin on 2007-10-31
Try using:
rootnoverify (hd0,0)
instead of:
root (hd0,0)

---

### Post by eyelessfade on 2007-11-08
Still no joy. It only reboot when I try to start windows. :/
have to use windows bootloader still.

---

### Post by Nebvin on 2007-11-08
I checked mine just to see what I have exactly, and I use:

title Windows
rootnoverify (hd0,0)
chainloader +1

I'm using vista 64 and ubuntu 64 with all drives on AHCI like yourself, so no idea what else it could be.

Although it could be an issue with the drive order being different in linux then it is from the bios (which can be the case if some drives are hd? and some are sd?). Usually in that case you'll get some sort of error message though. You could try editing the boot item while the menu is up (press e instead of enter) and try using tab-expansion to see if you are getting any clues to whether it thinks Windows is on hd0,0. For example, try changing the line to

rootnoverify(hd

and pressing tab to see your options, put in 0 (or any other ones that come up) and try the same with the second number. Any NTFS partitions should come up as unknown partition type I believe.

But if the Windows bootloader is working out okay, no harm in using it. Less chance of windows overwriting it in case of a reinstall and having to get the ubuntu cd back out to change back again.

---

