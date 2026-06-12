---
title: "Dual booting (1st) Ubuntu &amp; (2nd) OS X (Tiger)"
date: 2006-03-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by akcom on 2006-03-20
I have a PowerBook G4 that I tinker with.  Eventually I fell in love with Ubuntu and run it constantly.  Over the time I've accumulated some important files and at the same time I've found that some of my favorite software (D compiler specifically) runs only on OS X.  I would like to dual boot the two, but I'd like to preserve my current Ubuntu installation and install OS X second.  Is this kosher?  Will OS X wipe my partition table completely or is there some way I can install OS X and keep a certain partition "safe"

thanks in advance,
Alex

---

### Post by aimislame15 on 2006-03-20
You have a very interesting predicament. You see, OS X typically refuses to be installed second on a hard drive. It is possible to make a system dual boot going from OSX and adding Ubuntu, but the opposite, hasn't really been worked out. Good luck, Eric

---

### Post by grazie on 2006-03-21
OSX can be installed on any HFS/HFS+ (or more rarely UFS) partition with enough space. The problem you've got is that you can only create HFS/HFS+ partitions with OSX and like you say OSX wipes the disk to do so. You're only options are to backup (there are lots of ways) Ubuntu and copy back to the hard drive after you installed OSX or maybe install OSX on an external **firewire** hard drive.

---

### Post by jdp on 2006-03-21
If you use **parted** to resize your Ubuntu install from the Install or LiveCD and leave space for OS X to make a partition it might work.  When you boot the OS X install CD/DVD you can go to the menus and start the Disc Utility and create your own HFS+ partition.  OS X **will** let you pick what partition to install to, and not just format the whole drive by itself, so long as you have an HFS+ partition avialable to install to.

---

### Post by ssam on 2006-03-21
sorry to offer a third conflicting opinion, but i think you can do this.

if you boot from an ubuntu live cd then you should be able to use gparted to resize your ubuntu partition and create a HFS+ partition. then mac os x should be able to install into that HFS+ partiton. the mac os installer will most likely disable yaboot, but you can fix that with the instructions [https://wiki.ubuntu.com/YabootConfigurationForMacintoshPowerPCsDualBoot](https://wiki.ubuntu.com/YabootConfigurationForMacintoshPowerPCsDualBoot)

another thing you could do it to use Mac-on-Linux. you could create a disk image file in your ubuntu patition and install mac os x on it using MOL. have a look at [https://wiki.ubuntu.com/MacOnLinuxHowto](https://wiki.ubuntu.com/MacOnLinuxHowto)

---

### Post by jdp on 2006-03-21
I'll second the use of MOL.  It's been a while since I last had the setup, but I did have Ubuntu as the main boot partition on an iMac G3 350.  OS X was on another partition, but Ubuntu was default.  I installed and config'd MOL, and set MOL to load the OS X partition directly.  It worked wel enough that I could use FireFox or Safari to view Flash content.  By having the proper modules that are supposed to be included in Dapper, setting up MOL should be much easier.

---

### Post by grazie on 2006-03-21
ssam, What tool do you use to format partitions to HFS+ from Linux?

---

### Post by ssam on 2006-03-22
[QUOTE=grazie]ssam, What tool do you use to format partitions to HFS+ from Linux?[/QUOTE]

i think gparted (gnome partition editor) can do it. its included on the live cds.

---

