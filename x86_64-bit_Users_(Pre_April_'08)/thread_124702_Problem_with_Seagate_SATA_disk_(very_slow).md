---
title: "Problem with Seagate SATA disk (very slow)"
date: 2006-02-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by MF_III on 2006-02-02
Hi all, i have Kubuntu 5.10 Breezy (AMD64) and i have aproblem with my sata hard disk. It is a Seagate model ST380013AS 80GB SATA and in this disk i have Kubuntu in ext3 fs. My problem is that disk is very slow because when i try to cut a folder with many songs and paste it to an other place but in tha same disk the progress it is very slow like copy (it takes 7-10 minutes to cut 1000 songs :() and when i try to write a data dvd instead of 8x speed that i choose, K3b is writing the dvd about 3.8-4x speed :( and in the gkrellm the disk is full (5-6MB)

I tried to enable dma to disk but i take this message:

# hdparm -d1 /dev/sdb

/dev/sdb:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device


Whatever, also i see that dma is enabled on SATA disks....

Then, what is wrong? Seagate?

My system is:
DFI LanParty SLI-DR
AMD64 X2 Dual Core 3800+ 2.00Ghz
2x1GB G.Skill RAM

I am waiting your answers... Thanks! (sorry if my english are bad)

---

### Post by CyberAngel on 2006-02-05
[QUOTE=MF_III].....and when i try to write a data dvd instead of 8x speed that i choose, K3b is writing the dvd about 3.8-4x speed....
[/QUOTE]

That might be a k3b problem....

I have the same problem too but my SATA Seagate 200GB is not slow (I have seen on gkrellm 30MB/s a few times)

When I am using NeroLinux it burns the DVD even on 16x!!

---

### Post by yorick on 2006-03-31
I've had a similar thread some month ago:
[http://www.ubuntuforums.org/showthre...a+working+slow](http://www.ubuntuforums.org/showthre...a+working+slow)

It seems in my case it is an unfortunate combination of hard-drive/controller, and I have to wait until a fix is found...

Hope you have more luck...

As for the k3b problem, it is indeed related to k3b. Try setting the speed to "ignore" and it will write the dvd's at the maximum speed the dvd disk you are writing on supports.

---

### Post by CyberAngel on 2006-04-09
[QUOTE=yorick]As for the k3b problem, it is indeed related to k3b. Try setting the speed to "ignore" and it will write the dvd's at the maximum speed the dvd disk you are writing on supports.[/QUOTE]

Doesn`t work faster than 4x-6x (The Maximum speed is 16x both for my DVD Writer and the Blank Disc I am inserting to burn to) even if I set speed to "ignore"...

---

