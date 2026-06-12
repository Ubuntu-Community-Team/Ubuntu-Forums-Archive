---
title: "Breezy installer can't recognize CD on Old World Box"
date: 2005-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by lazloman on 2005-11-14
Title says it all. I can boot with BootX just fine, but after the language support questions, a message appears saying that the CD is not an Ubuntu CD. I've burned the CD at 1x, 2x, and 4x using  Disk Utility on an OSX box and get the same result at the same point each time. When I boot this box into OS 9, the CD mounts just fine. Any ideas?
TIA

---

### Post by ssam on 2005-11-14
just a quick check: you burned the image to the disk, not as a file on the disk.

on an oldworld mac i would recommend that you gave yellowdog a try. they have been in the business of linux on macs for many years.

---

### Post by lazloman on 2005-11-14
Thanks for the reply, but I checked the YD site and they don't seem to support Old World box. Unless I missed it somewhere, they only list New World types.

---

### Post by jshamlet on 2005-11-15
[QUOTE=lazloman]Thanks for the reply, but I checked the YD site and they don't seem to support Old World box. Unless I missed it somewhere, they only list New World types.[/QUOTE]

Yellow Dog *no longer* supports OldWorld machines, but you can still download YDL 3.0.1, which does.

However, you have to ask yourself if you want to go with a solution you know is a dead-end up front.

That's one reason I went with Ubuntu - it is one of the few distros that still supports older Macs. (I got my G3 MT for free - though I blew $20 for an Acard  ATA-133 card, and $25 for a faster G3 processor)

---

### Post by stuporglue on 2005-11-15
I think our problems have the same root cause.

The old Macs use scsi drives, and it seems that not all of the right scsi drivers are complied into the kernel. In my case, I was able to install, but when I try to boot using the kernel from the install, it can't find the boot disks. 

Do you get dropped into busybox? If you do, try modprobing mash and sd_mod, then running udevstart. At that point, you may be able to get the CD mounted...though I don't know how to start the installer from there. :-) 

I'm going to try to compile a custom kernel with the drivers needed by oldworld machines. I haven't compiled a kernel in quite a while though, and I don't know exactly which drivers are needed so I suspect it will take a week or more to get it right.

---

### Post by stuporglue on 2005-11-15
Try this:

Before answering any questions (ie. before hardware detect) go to a second console and run:

modprobe mesh
modprobe mace
modprobe sd_mod
udevstart

Then return to the installer and see if it works. That might load the drivers you need to access the CD and the disks.

---

### Post by lazloman on 2005-11-16
Thanks for the replies everyone. Anyway, I tried the last reply and still got no love. The installer says the CD is not an Ubuntu CD. I originally downloaded the ISO from Safari, that may have been a mistake. I'll try curl and see if maybe the CD is just not readable...


...oh well. Back to Gentoo I guess

...but wait! Never give up! I downloaded the ISO on a Windows box using Firefox, made the CD w/Easy CD Creator and now the installer is installing the base system. I did not have to manually load any modules, its just worked! Cool!

Anyone know why burning from the Finder did not work? I used curl to download the last Mac (10.3.9) burned version.

---

