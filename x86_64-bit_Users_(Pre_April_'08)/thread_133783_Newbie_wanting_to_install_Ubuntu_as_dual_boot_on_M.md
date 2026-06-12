---
title: "Newbie wanting to install Ubuntu as dual boot on Mac Mini"
date: 2006-02-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by mer45 on 2006-02-20
Hi all,

I'm a Windows user who is new to both Macs and Ubuntu.   I just bought a Mac Mini and want to set it up to dual boot both OS X and Ubuntu in order to learn both systems.  Help!  Would somebody take pity on me and guide me through the process?  I have figured out how to make the bootable Ubuntu cds, am running the Live CD now, and am trying to figure out how big to make the partitions and then, well....how to do it.  I understand the Mac disk utility but what next????

Thanks for any help,
Meredith

---

### Post by Jedeye on 2006-02-20
I have not installed ubuntu on a mac before but as you work your way through the install cd it will come to a section about partitions. and you can set it there... its will move your mac data(not delete anything) and then create the partition. Be sure to read carefully when you get to that section. As far as how much space you should have well that depends on how much you think you need... consider music pictures etc.. and how big your drive is. I would concider how much I think I will want to use in OSX and then take whats left over and use that for ubuntu. You have 2 great operating systems so have fun with them!

---

### Post by mer45 on 2006-02-20
Hi Jedeye,

Thanks for responding.  Are you saying I don't have to wipe the hard disk or set up partitions and then reinstall OS X on one of them first?  I may be just too new to do it without a play-by-play.....

Meredith

---

### Post by linear on 2006-02-20
Here's what I'd recommend. First read these:

[https://wiki.ubuntu.com/Installation/PowerPC]("https://wiki.ubuntu.com/Installation/PowerPC")
[http://www.askdavetaylor.com/how_do_..._mac_os_x.html]("http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html")

This worked for me:

0. Read up in the PPC forums on any model specific quirks.
1. Back up OS X partition. ([Carbon Copy Cloner]("http://www.bombich.com/software/ccc.html") works well.)
2. Repartition disk. Make two partitions, leave first as free space and second for OS X. Disk Utility is destructive (another reason for the back up), or there is a howto [here]("http://ubuntuforums.org/showthread.php?t=89960") on using **parted** to resize non-destructively. Make the partition at least 5GB, but bigger is better if you really plan to use it.
3. Boot from the Ubuntu install disk. When you get to the partitioning step, tell the installer to use the largest free space. It will take care of the rest.

---

### Post by Tipo on 2006-02-21
Yes, I would also recommend that you back up the original Mac partition to an external drive before you start, you never know what can happen.;)

---

### Post by mer45 on 2006-02-21
Thanks so much guys.  Wish me luck...
Meredith

---

### Post by jdp on 2006-02-22
No need to wipe and repartition: [Repartition with the Ubuntu CD for free](http://ubuntuforums.org/showthread.php?t=89960&highlight=partition+hfs+free)!  Bck up any file you don't want to lose to a possible mishap, then go to it.  I've repartitioned an OS 9 Mac and my OS X iBook.  I plan on doing my Mini after Dapper comes out.

---

