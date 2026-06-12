---
title: "Cant Get it to boot"
date: 2006-07-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by will71110 on 2006-07-01
I am a first time Linux user. I have loaded from the live CD and I like the OS so I loaded Ubuntu 6.06 on my computer .   The install went fine.  Now when I try and boot from the Hard drive after I installed it, I get "error loading operating system". This is what I have hardwear wise:

-CPU AMD 64 3200
-MB ECS MPV KA1 (ATI 200 W/ ATI 450 SB Chip set)
-2 Plextor CDroms.  Ones a DVD/rw and the other is a CD/RW
-3 Hard drives.  75 GB Rapter Western Digital - 200 GB Western Digital and 30 GB western digital (which is where uduntu is installed).
-ATI MSI x1600 Pro Video Card
-Soundblaster Autigy 2 Platium
-500 watt PSU
-2 Dual channel( 4 ram chips) OCZ DDR400 CAS T-2-2-2-5

Anyone have any ideas of what I have done wrong? 

Thanks

---

### Post by bikeboy on 2006-07-01
Which hard drive is set to boot from in the bios? What you want is for the hard drive with the Ubuntu boot loader (GRUB) to be the one that's booted from, then it will allow you to select windows or Ubuntu at boot time.

---

### Post by will71110 on 2006-07-01
I use F11 (Which is the bios option to choose a boot before anything loads) to choose which hard drive to boot from.   I tried installing GRUB on the boot drive with windows but it didn't install.  Windows boots up as normal.    Unless it thinks that my 200GB Hard Drive is the first bootable drive.  This could be because my 75GB is a SATA drive.  But there is not a windows on the 200GB,  just a file system in NTFS.  I really dont know though.

---

### Post by bikeboy on 2006-07-01
Ok so GRUB didn't install anywhere? Because I think you need it to boot Ubuntu, windows' boot loader doesn't acknowledge that other OS's exist. You can attempt to install GRUB even after the main install. I don't know how though :(

---

### Post by will71110 on 2006-07-01
Ok I just tested it.  GRUB installed on the 200GB drive.  It wond load though, I get an error 17.  There is no windows on that drive though.  There use to be but I have formatted that drive before I started using it as only a File System drive.  I attempted to install the OS under the OEM install and it did give me a chose to install GRUB on a drive but I dont remember it saying anything about the drive with Ubuntu installed.

 I'll have to attempt it again to see if it was there and I overlooked.  It did though have the SATA drive listed but I'm afraid of installing it on with windows since I had a time with windows before hand.  (Mainly had to do with a BIOS setting I have to confugure Manually)  I'll try the OEM install again and let you know how that turned out.

---

### Post by will71110 on 2006-07-01
Well GRUB install (had to choose hd1 when I installed the OEM install) but now when I choose Ubuntu to load I get a error 17, unknowned file system.  Any ideas of what to do about that?

---

### Post by bikeboy on 2006-07-01
Try having a look here. it seems like a similar issue.
[http://ubuntuforums.org/showthread.php?t=196544](http://ubuntuforums.org/showthread.php?t=196544)

There's a few others about error 17 eg.
[http://ubuntuforums.org/showthread.php?t=198719](http://ubuntuforums.org/showthread.php?t=198719)

---

