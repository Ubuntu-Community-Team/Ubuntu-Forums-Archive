---
title: "How to dual boot Ubuntu and Windows XP?"
date: 2006-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by girionis on 2006-03-10
Hello, I have already installed Ubuntu 5.10 on an AMD 64 bits processor. I would also like to install Windows XP mainly for game playing (I have several issues trying to play games using VMWare). Are there any instructions on how to dual boot my computer when I already have Ubuntu installed? I would like to keep the installation of Ubuntu and install Windows on a separate partition. Any guidelines or links would be appreciated.

Thank you

Regards

Panos

---

### Post by Cyclone268 on 2006-03-10
Yeah, I'm too wondering the same thing and would like to get an answer.

Thanks

Oliver

---

### Post by astyanax on 2006-03-10
When you do install Windows XP, the Windows bootloader will overwrite your Linux bootloader (GRUB or LILO), so you won't be able to boot into Ubuntu.  What you can do is use a Ubuntu-Live CD and reload GRUB.  This should overwrite the NT Bootloader and allow you to setup a dual boot.
Command:  sudo grub-install /dev/hda  &#61664; Assumed that /dev/hda is the location of /boot partition
NOTE:  The NT Bootloader has the capability of setting up a dual boot but most of the information I've seen on the Linux forums does not recommend this approach.

Download link: [http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/]("http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/")

---

### Post by Cyclone268 on 2006-03-10
Well, Im actually in a bit of a diiferent situation.. I have windows XP right now, and am going to be installing linux soon... Could you give me info on that?

P.S.-Srry to take over ur thread lol

Thanks

Oliver

---

### Post by astyanax on 2006-03-10
If you have Windows XP installed already, it's a cakewalk.  You just install Ubuntu with the regular install CD and during the installation process it will ask you if you want to install GRUB as your bootloader.  Just say yes and GRUB should auto detect Windows for you and set up the dual boot.

---

### Post by Klaidas on 2006-03-10
Check the first link in my signature :)
For insrtalling windoze: it will overwrite your MBR, but you can restore it : [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

### Post by astyanax on 2006-03-10
That has got to be most thorough step-by-step installation doc I have ever seen for a Linux installation.  I just thought I'd give you props on it. :)

---

### Post by girionis on 2006-03-11
Right, thank you all for your help :)

Problem now is that I only have one partition, that is where Ubuntu is installed, how can I create a separate partition where I can install Windows on. I tried fdisk but I got some warning messages and the changes I made to the hard disk were not preserved.

Thank you

Panos

---

### Post by dave_567 on 2006-03-11
I recomend that you start out with a clean installation of win XP first and then place Ubantu on after.  Each operating systen must have its own partition to work out of.

I was just doing this on a system that I ws piecing together.  Bad things can happen when you play with the boot sectors.  Read up before acting.  For tools to partition you can try UBCD.  It has just about everything you could need for this or any other thing you might want to try out.  This is the link. 

         [http://ubcd.sourceforge.net/](http://ubcd.sourceforge.net/)

Take it slow.  partitioning can go verry bad if not done correctly.  But getting out of the problems is half the fun...

---

### Post by stupidStan on 2006-03-11
when I set up my new opteron (64) machine, i partitioned before I installed anything.  I then installed XP, not I want to put Ubuntu on another partition, is there anythign I need to do other than stick it on the other partition and tell grub to dual-boot?

---

### Post by IcyEars on 2006-03-16
One thing to bear in mind when partitioning is that you may want to create a separate Fat32 partition in case you ever need to transfer files from Ubuntu to Windows XP (if XP is going on an NTFS partition) since Ubuntu won't write to an NTFS partition (as far as I have found, anyway).

With a separate FAT32 partition, XP can read and write to it as can Ubuntu.  it acts as a kind of DMZ between the two.  I'm using mine to share Thunderbird and Firefox between the two.

---

### Post by shinji257 on 2006-03-16
Something else that I have found.  If you have Windows XP already installed and also have Partition Magic installed then you should probably go ahead and use that to partition and format the drive in advance.  You can assign the partitions during the installation.  I found that during the formatting bit the drive geometry values get a bit weird and Partition Magic will complain about it.  In fact it will show the drive as bad sometimes depending on if the installer created the partitions or not.  Partition Magic supports EXT2 and EXT3 partition types (it can create and format them).

---

