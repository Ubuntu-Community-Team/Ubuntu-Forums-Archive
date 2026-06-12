---
title: "Grub Issue, cannot boot w/o external drive"
date: 2008-09-27
forum: openSUSE and SUSE Linux Enterprise
---

### Post by osabr22000 on 2008-09-27
I'm fairly new to linux,and recently did an install for OpenSuse 11 to an external usb hard drive.  The type of drive is a Western Digital 300 GB usb drive and my laptop is a Dell Inspiron E1705/9400 with Windows Media Center installed.  It appears that I did the install to my external drive properly, since my system goes to that GRUB menu when my hard drive is connected at boot up.  However, I receive an error if I start my laptop with out connecting the hard drive first, which means I cannot start Windows.  I can start Windows when I connect the USB drive, go the the GRUB menu then select Windows.  Is there any easy way for me to fix this so I can access windows w/o connecting the external drive?  If so, please be very specific with the steps I need to follow.  Thank you so much for helping.

---

### Post by L815 on 2008-09-28
It's simple really :)

You said you installed on your External HDD, which means GRUB is on there as well. 

The easiest solution is to get a Windows Install Disk, and fix the bootloader (in the repair options). 

For Xp after booting the install disk and entering the repair mode, type in the command line : fixmbr

For vista, do the same only you have to type : bootrec.exe /fixmbr

This will fix Windows bootloader, and Grub will still work when you plug in your External HDD!

---

### Post by osabr22000 on 2008-09-28
It worked... kind of.  I can boot to Windows just fine without having my external USB  hard drive connected.  :)  But now I cannot boot from my USB HD into Linux.  I keep getting the error:
"No bootable devices--strike F1 to retry boot, F2 for setup utility
  Press F5 to run onboard diagnostics."

The type of computer is a Dell Inspiron E1705.  I also tried booting from each of the six USB ports and it's the same error.  I've tried doing it through the "One time boot" menu, and I've also disabled all boot options but the usb...  Can you help me with that one also?

---

### Post by L815 on 2008-09-28
This issue is a bit more complicated, but it should be fixable.

First, you will need a Ubuntu Live CD.
Boot up into the Live CD and plug in your External HDD.

Now, you will need to know the path to your external hdd. For example, hd0,0 is the first partition on the first hard drive.
It will be different for your external hdd.


Open up terminal and type:
sudo grub
(password enter here)
root(hd0,0) (replace hd0,0 with your external hdd)
setup (hd0) (here only replace the external hdd alias, not the partition number)
exit

Now grub will be reinstalled onto the external HDD, and it should be bootable.

---

### Post by osabr22000 on 2008-09-29
L815, I truly appreciate all of the help you've provided me so far.  I just wanted to know if the grub installed from the Ubuntu disk will look different from the one on the Opensuse disk I have.  I only ask because Suse's grub is asthetically pleasing.  If it would be different would you know how to install the grub from the Suse disk?  If not, that's okay I'll just reinstall grub from my Ubuntu disk.  Either way thank you so much for your help.

---

