---
title: "Someone(s) please help me!"
date: 2007-10-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by ntdsone on 2007-10-12
Hey everyone,

I'm using Kubuntu Edgy on my system.  I'm somewhat new to this, hence my posting of a big problem I'm having.  During a big system update, (I believe it was upgrading the entire Ubuntu OS), the entire system froze, and I was forced to reset on my computer.  Consequently, the results were fatal.

The system can't boot normally.  It loads for a bit at the Kubuntu loading screen, but then it freezes along the way.  So I restart and select the recovery modes that Grub displays.  The system begins to load lots files and throws them on the screen as normal.  And then it freezes.  The last line on the screen when it's freezing is the following:

Setting up console font and keymap...

The entire console font on the screen changes as desired when this operation is executed, but nothing else happens.  I've let the system sit there over night and yet nothing has changed since.

This only happened AFTER the incident of the system freezing during a system update.  

I've had this problem since June, and have been using other operating systems ever since, but I hope this is enough information to draw some help!

Here's my system information in case anyone needs to know:

AMD Athlon x2 3800+ 2.0GHz
2GB (512MBx4) DDR2 PC5300 667MHz
2x160GB 7200 RPM Seagate Hard Drive
80GB 7200RPM Maxtor Hard Drive 
Asus M2N32-SLI DELUXE Motherboard
Nvidia 256MB 7600 GT x2 SLI
(3 HD's configured as JBOD)

Any kind of help would greatly be appreciated! :KS Thanks!


Mark

---

### Post by Kilz on 2007-10-12
> **ntdsone said:**
> Hey everyone,

I'm using Kubuntu Edgy on my system.  I'm somewhat new to this, hence my posting of a big problem I'm having.  During a big system update, (I believe it was upgrading the entire Ubuntu OS), the entire system froze, and I was forced to reset on my computer.  Consequently, the results were fatal.

The system can't boot normally.  It loads for a bit at the Kubuntu loading screen, but then it freezes along the way.  So I restart and select the recovery modes that Grub displays.  The system begins to load lots files and throws them on the screen as normal.  And then it freezes.  The last line on the screen when it's freezing is the following:

Setting up console font and keymap...

The entire console font on the screen changes as desired when this operation is executed, but nothing else happens.  I've let the system sit there over night and yet nothing has changed since.

This only happened AFTER the incident of the system freezing during a system update.  

I've had this problem since June, and have been using other operating systems ever since, but I hope this is enough information to draw some help!

Here's my system information in case anyone needs to know:

AMD Athlon x2 3800+ 2.0GHz
2GB (512MBx4) DDR2 PC5300 667MHz
2x160GB 7200 RPM Seagate Hard Drive
80GB 7200RPM Maxtor Hard Drive 
Asus M2N32-SLI DELUXE Motherboard
Nvidia 256MB 7600 GT x2 SLI
(3 HD's configured as JBOD)

Any kind of help would greatly be appreciated! :KS Thanks!


Mark

I hope you backed up all important documents before installing a beta version. Because I have a feeling you are going to now reinstall the operating system. If you have a home partition you might be able to save some things. You might also want to try and install to another partition. That way you could mount this failed install to a folder and copy over any files/documents you may need.

---

### Post by Jouke74 on 2007-10-12
Yup, no clue of things which got damaged, no idea which parts are updated and which not. No info about configuration files that need to be fixed. If you really want to restore the system it is going to take lots of time with no idea if the result will be stable. A reinstall will be easier, or maybe a recovery install (I never tried that on the Alternate CD). Anyway, before reinstall load up the live CD (so the CD runs the OS) and copy all important files of your disk.

---

### Post by crjackson on 2007-10-12
> **Jouke74 said:**
> A reinstall will be easier, or maybe a recovery install.

Please explain what a recovery install is and how does one go about doing that.

---

### Post by ntdsone on 2007-10-13
Yeah... I was afraid of that.  The issue is, I do have some important files on that volume that I do need backed up.  I have tried running the LiveCD version, but I failed at mounting the correct partition which contains such important files.  I know for certain that its on [FONT="Courier New"]/dev/sdc[/FONT].  

How would I go about backing up my files by using a LiveCD?


-mark

---

### Post by ntdsone on 2007-10-13
Oh, and I remember what kind of upgrade it was now.  It was an upgrade from Edgy to Feisty that failed.

-M

---

### Post by init1 on 2007-10-13
> **ntdsone said:**
> Yeah... I was afraid of that.  The issue is, I do have some important files on that volume that I do need backed up.  I have tried running the LiveCD version, but I failed at mounting the correct partition which contains such important files.  I know for certain that its on [FONT="Courier New"]/dev/sdc[/FONT].  

How would I go about backing up my files by using a LiveCD?


-mark
No, your hard drive partition cannot be on /dev/sdc. Did you mean /dev/sdc1? Do a
```

fdisk -l

```

---

### Post by maddogshug on 2007-12-25
Ok, I'm sure i'm too late to help you, but i encountered the same problem and fixed it. I was updating my gf's wee sisters comp, left , and apt-get had a problem. she rebooted leaving it unusable. I booted a gentoo minimal live cd [http://www.gentoo.org/main/en/where.xml]("http://www.gentoo.org/main/en/where.xml")

your partitions  will probably be different


setup network

#net-setup eth0

mounted system

#mount /dev/hda3 /mnt/gentoo
#mount /dev/hda1 /mnt/gentoo/boot
#mount -t proc none /mnt/gentoo/proc
#mount -o bind /dev /mnt/gentoo/dev

copy network settings 

#cp -L /etc/resolv.conf /mnt/gentoo/etc/

and enter ubuntu

#chroot /mnt/gentoo /bin/bash

fix dodgy package

#apt-get remove *broken packages* 

and finished update

#apt-get update

System works again, any live cd would probably work, gentoo has all the required tools and is a small download
Hope this helps someone

---

