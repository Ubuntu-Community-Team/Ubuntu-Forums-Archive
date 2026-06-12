---
title: "install freeze (early on)"
date: 2006-10-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by realpro on 2006-10-02
Hi,
I'm building a new machine, and (am/was?)planning on running Ubuntu on it.  But... Here are the details: using the AMD64 alternate CD, the MB is Gigabyte 570 based /socket AM2.  CPU is AMD 64 2x 4200, video is nVidia 7600GT (silent), 4x500G SATA RAID5 disks, 2G RAM (tested OK!!!) etc. etc.  Problem is -- the install freezes after I select (any) of the install options -- last line is the PARPORT0 parameters (irq, DMA etc).  I tried adding the "nosplash" and "nomce" parameters, as someone suggested in another post, to no avail.  I was able to get to a root prompt if I used the BOOT_DEBUG=3 params, but no further (it skips the full boot detection sequence -- or so it seems).   HELP???!!!! Please...

Erez

---

### Post by amitbiswas on 2006-10-02
Hi, I am facing the same problem with same hardware situation except motherboard ASUS M2N-E, I have tried several things but sofar no go.... please help any one knows the reason....

---

### Post by manngar on 2006-11-27
I'm having trouble as well. I'm using the EdgyEft Alternate CD for x86_64. I have an Asus M2NPV-MX with an AMD X2 3800 AM2 CPU. I've got 4Gb DDR 800 RAM installed and 4 x 500Gb Seagate NL35 hard disks connected to the mobo SATA ports. I'm using the integrated nForce 6150 graphics and 430 I/O.

With one disk active everything is fine, the system is stable. As soon as I try to build a RAID array however, I run into problems. Software (i.e. mdadm) RAID5 (3 disks) is a non-starter, the machine freezes (with display corruption) during the sync phase. With RAID1 (2 disks), I can build an array, but as soon as I copy from one of the other disks (e.g. the OS drive) to the array, I get the freeze problem. 

It's tricky to diagnose, as by the time it freeze the console is locked up and there is nothing to do other than reboot. I've checked all component temperatures, and everything is fine, so I don't suspect an overheat.

I've tried Fedora 5 and 6 and have the same problem. With FC5 I could build a RAID1 array, and I did have it stable for a while, but didn't try copying data between disks.

Could it be that as soon as you try to access more than two disks under heavy load you get the problem?

Right now I'm stuck with all these drives and no means to use effectively them in a RAID array (which is why I bought them).

Hope someone can help - personally I'm thinking of either buying a different SATA controller (with a different chipset) or an entire new motherboard (which may be cheaper).

Gary :(

---

### Post by manngar on 2006-11-28
So - I've got things working. It turns out that my problem was too much RAM. I took out 2Gb, leaving 2Gb installed, and hey presto - the box is now stable. I guess there's a problem with a lack of 32 bit address space for I/O or DMA or something. Perhaps even the video frame buffer.

Gary

---

### Post by laberti on 2007-02-22
Hey guys,

I'm trying to install as well, without success. Does anyone knows how install an linux 64 distro without taking out the memory??

Cheers,
Leandro

---

