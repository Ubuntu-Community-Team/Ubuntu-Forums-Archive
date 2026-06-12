---
title: "Can I have Mac &amp; Linux without delete anything?"
date: 2006-03-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by yuvalsarig2005 on 2006-03-03
Can I install Mac & Linux on same computer, without change or delete anything?

Please Answer

---

### Post by el3ktro on 2006-03-03
So I suppose you now have a computer with Mac OS installed? Well I don't know if there are any partitioning tools that can make a Mac OS partition smaller, or if perhaps the Mac OS installer supports that. If there's no such tool, then you're lost ...

Tom

---

### Post by BoneKracker on 2006-03-03
What do you mean by "without delete anything"?

You can set you system up to dual-boot between MacOS and Linux, if that's what you mean.  Some ways to do that are:

a) add a new hard disk and install ubuntu on that
b) resize your existing partitions to make room for ubuntu on current hard drive(s)
c) backup your data from your current MacOS system, create a new partition map, reinstall MacOS on a smaller parition and restore your backed-up data, and install ubuntu.

"mac-fdisk" can be used for partitioning.

- If your disk is getting full, (a) may be best.  
- I personally don't even know how to resize HFS/HFS+ partitions but am pretty sure it's possible; if you're comfortable doing that and have space on your drive(s), you may opt for (b).
- If your MacOS installation is old and could use a "spring cleaning" anyway, you may want to opt for (c).

Also, if you just want to try out ubuntu, you can get the Live CD, which doesn't install anything.  Then if you like it, you can install it.

---

### Post by linear on 2006-03-03
If you choose to resize your Mac partition, there are instructions here:
 
[http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960)

---

### Post by Rob Friefeld on 2006-03-03
I have OS X on a 60GB hard disk and successfully followed the instructions ([http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960)) for repartitioning (giving 20GB to Ubuntu). It took a **long time** to repartition. Have patience. Then I finished the Ubuntu installation. The first time, the second stage of installation hung at 57% complete. I ran the installation again and it went well, again taking well over an hour on my machine.

Mac OS X was unaffected. When you restart or turn the machine on, you are offered a choice of "press l for Linux" or "press x for OS X", and that's all there is to it.

Before doing all this, I backed up everything I would really hate to lose (such as my photo library!) But, no problems.

---

### Post by spaceballl on 2006-03-06
Use "parted." Search the forums for a tutorial.

---

