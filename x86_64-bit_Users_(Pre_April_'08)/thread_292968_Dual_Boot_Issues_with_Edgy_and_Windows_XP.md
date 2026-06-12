---
title: "Dual Boot Issues with Edgy and Windows XP"
date: 2006-11-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by EmyrB on 2006-11-04
Hi all,

I have an AMD 64 bit PC which has 2 HDD's installed. The first is 160GB and has 4 partitions and this houses Windows XP. The disk was upgraded to dynamic and the file system on each of the disks is NTFS.

The second disk is a 40GB and this has 4 partitions which houses Edgy Eft, the file system is Ext3 on 3 partitionsd and the fourth is a swap.

Installed Edgy with no problems, set up the partitions and grub was installed to hd0. Rebooted my PC and my Grub menu list came up with Ubuntu and Windows XP listed.

Booted into Edgy with no problems, set up my desktop enviroment, installed the NVidia driver and setup Beryl and XGL and everything is working great. The only thing I cannot do is mount my Windows disks, I am sure this has something to do with it being a dynamic disk, fdisk -l shows them up as SFS insted of NTFS.

Anyway, I had to boot into windows as my e-mail is currently being read with Thunderbird. Downloaded my mail and after I had finished, I rebooted my PC. Now instead of bringing up the Grub menu list, it reboots. And that is all it does, just reboots.

The "Loading Grub, Please Wait" message appears then the PC reboots. Now if I boot with an old Windows 98 CD and do a fdisk /mbr I will restore the M$ mbr and I won't be able to boot to Ubuntu.

Any ideas why after booting into Windows I can no longer go past the Grub Loading bit and then the PC reboots?

Cheers

EmyrB

---

### Post by EmyrB on 2006-11-04
Quick update :-

Booted using the Ubuntu Install CD and opened a terminal. Typed sudo grub and got to the grub command.

did a setup (hd0) and then rebooted PC.

I have now a working PC. Booted to Ubuntu and then rebooted, grub menu list came up. Booted into Windows XP and then just rebooted and PC reboots constantly after the "loading grub, please wait" message.

So it is definitely something that Windows is doing to my MBR.

Maybe its a sign from the linux gods to switch over to Linux full time :)

If anybody has any ideas, I would be eternally greatful.

Cheers

EmyrB

---

