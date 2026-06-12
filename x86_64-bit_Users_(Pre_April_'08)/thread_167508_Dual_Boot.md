---
title: "Dual Boot"
date: 2006-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Prasad007 on 2006-04-28
i have i Hard disk 160 gb with 2 drives c and d 80 gb each. i have windows on c if i try to install linux on d it partitions the whole hard disk and formats it.

what do i do?
please help!
Thank you!

ps. this is my very first experience wid linux.

---

### Post by jazzmuzik on 2006-04-28
Have you ever used partitioning software?

---

### Post by Prasad007 on 2006-04-28
thank you for ur reply.
no i havent i only manage partitions using windows xp installation.

---

### Post by jazzmuzik on 2006-04-28
From what I gather, the Ubuntu Breezy 5.10 installer has the ability to partition your hard disk, including shrinking the Windows partitions to give you room to install Linux. Maybe somebody else can confirm or deny this.

Anyway, here's the general procedure:

1. With partitioning software make the windows partitions smaller so you gain enough free/unused space in which to install Linux. Generally, about 6 gig is sufficient free space, but more is helpful if you plan on storing lots of files or music. (You can also utilize Windows drives for storing data like music, but the Linux OS itself needs it's own partition.)

2. Once you have the free space, tell the Ubuntu installer to install the operating system to that free space.

---

### Post by Prasad007 on 2006-04-29
so can i not install it on d drive. windows is on c.
secondly, how do i "tell the Ubuntu installer to install the operating system to that free space"" ???
that was the hardest part.... the partitioner....

---

### Post by tymek666 on 2006-04-29
Well, You can prepare patitions even under winxp with partionmagic f.e. or just delete partition d: without resize partition C. And then run ubuntu cd.

---

### Post by Prasad007 on 2006-04-29
oh so that means theres no point formatting d drive is there? i need to leave that space unpartitioned so that linux can partition it.
can i do that without partition magic ? in windows itself ?

---

### Post by erico on 2006-04-29
[QUOTE=Prasad007]oh so that means theres no point formatting d drive is there? i need to leave that space unpartitioned so that linux can partition it.
can i do that without partition magic ? in windows itself ?[/QUOTE]

You might find it easier to leave your windows installation where you have it on your C drive.  Make sure that your Windows install is working and try it again. You can create partitions for your Linux install by leaving free space on the drive when you reinstall Windows. 
Choose expert install this time(type expert when the UBUNTU disk boots up) and go through the install procedure. When you get to the partitioning phase go into expert mode  and create a linux native partition and a small (@512 MB) Linux swap partition.Those two partitions are the minimum required for a Linux install.  _After the base package is installed and you are at the GRUB install phase choose to have grub install itself to the D drive and definitely not to the MBR of the C drive_. That should do it.  I have been playing around with multi booting for a while with Windows XP x86_64 / Windows XP 32 bit / Ubuntu.  This was the method I used to solve my own problem of Linux wiping out the Windows boot information in the hard drive's MBR. 
Good Luck and happy dual-booting ;)

---

### Post by Prasad007 on 2006-04-30
Thanks ! I got it myself in a different approach.
What i did was in windows xp install i deleted all partitions then made a c drive for windows and did not even partition the unallocated space.
then after installing windows , i installed linux on the unallocated space.
so both work fine it seems.
will this be fine?
secondly, that GRUB boot screen ... i dont like it really... can i have that basic windows screen that you get when u got many multiple windows installed ?
cuz GRUB has like 5 or 6 linux options and windows xp under other OS.
i dont want complications ..
thanks!

---

