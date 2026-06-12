---
title: "error during boot up, bad file system"
date: 2006-04-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by dereke on 2006-04-01
First, some background,
I have two sata drives, one that I want to dedicate to linux.  NTFS takes up all the space on my first Sata drive and the second is what I have available.  My goal is to install Ubuntu on the second Sata in such a way that the drive contains its own MBR and I can switch between linux and windows via my bios.  I did this by unplugging my first sata, installing ubuntu, then plugging the second back in.  I think ubuntu is confused with it's drive name now.  If I boot with windows unplugged everything is fine.  When i boot with it plugged in, it tales me I have a bad file system (and that it is not sure if the file system is ant ext3, etc...), but I am giving the option to continue anywas, which I do, and ubuntu still loads up.  Does anyone know where (and syntax) I can go to fix this problem of an error popping up during boot?  I thought it was a hard drive definition thing, but it still boots up to the correct hard drive and I am a little confused.

Thanks,
Derek

---

### Post by dereke on 2006-04-01
I just booted into Ubuntu.  I looked a little more carefully and saw that I received an error on boot up when the system "checks all file systems".  I think the system might be looking over the windows drive and not trying to boot from it and falling back to sdb by default, etc... I am not sure of the actual mechanisms going on  but I am questioning if my problem is what I thought it was.  The error is still annoying, because the rest of the boot is smooth and nice looking.

Thanks,
Derek

---

### Post by souki on 2006-04-01
I suppose grub root boot is refering to the first disk (hd0)
now, your disk is probably changed to (hd1)

if so, you just have to fix your /boot/grub/menu.lst
post it here, so we can understand a little more
can you see your windows partition from ubuntu ?
'df' output is needed also

PS: I've just noticed your second post, that's another problem

---

### Post by souki on 2006-04-01
[QUOTE=dereke]I just booted into Ubuntu.  I looked a little more carefully and saw that I received an error on boot up when the system "checks all file systems".  I think the system might be looking over the windows drive and not trying to boot from it and falling back to sdb by default, etc... I am not sure of the actual mechanisms going on  but I am questioning if my problem is what I thought it was.  The error is still annoying, because the rest of the boot is smooth and nice looking.
[/QUOTE]
I'm not sure of what you want to do and why you install this way (removing drive, etc...)
do you want the windows boot on the first disk and the grub boot on the second one ?
if so, why don't you use grub to boot windows ?

I think you cannot have windows mbr on the second disk, I mean by booting directly on to the second disk to the windows mbr (I'm not sure about that but I've never manage to it)
if you really want a windows mbr, you have to put windows on the first disk and install ubuntu on the second disk

---

### Post by dereke on 2006-04-01
My second post is an update to the first. I can see my windows hd in /dev, but not in any file manager in Ubuntu.  Also, when I went to /boot, it was empty.  I don't think it should be.  I am a new user and there is a lot of unkown out there but I don't think this is correct.  I am going to reboot and see if I can find out what is going on.  Also, about Grub, I have ahd a lot of trouble with it.  I first tried to install gentoo which was something... interesting... (compiled the kernel etc... but bootloader was giving me trouble).  I then tried to install fedora core 4 and ran into the same complications with the bootloader.  The windows bootloader always loaded + other complications when switching my boot drive.  I unplugged the drive and fedora core ran without a hitch, even after I plugged the drive back in.

edit:  Do you know how to load gfortran?

---

