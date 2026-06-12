---
title: "Configuring the bootloader"
date: 2006-04-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by CSMatt on 2006-04-22
I was able to successfully install Ubuntu and its bootloader on my iBook.  The bootloader recognized the existing Mac OS X partition and offers an option to boot from it.  However, the bootloader wants to boot to Ubuntu by default.  In contrast, I want the bootloader to boot Mac OS X by default (but I still want the bootloader to load by default rather than a direct boot to Mac OS X).  I would also like to set a 3 second time limit on how long the bootloader waits for the user to choose an operating system before automatically booting Mac OS X.

I remember when I was using Mandriva 2005 there was a graphical interface in the control panel that would change the bootloader options for you, but I see no such thing in Ubuntu.  I don't mind using Terminal and doing some manual editing if necessary, but I would still like to know how to do this.

---

### Post by MechaShiva on 2006-04-22
I have a similar question and figure it's better to post it here than on a new thread.  I have a pmac g5 that I would like to dual boot with linux.  I'm a long time linux user but I've never used it on ppc before.  So my question is, where is the boot loader written?  Is it written to the hard drive or is it some openfirmware voodoo?  

Here's the full scenario: I have a test hard drive that I would like to set up with linux to make sure my hardware works as expected but I don't want to resize/repartition my primary drive.  So my plan is to swap out my primary, throw in a spare hard drive and install it on there.  If it works as expected, I'll slave the test drive and dual boot it that way.  My concern is if the bootloader is written to openfirmware, when I put my primary drive back in, will it boot properly?  Or is the boot loader written to the hard drive in which case once I pull the drive out, no harm no foul.  

Also, if I pull the spare drive out, is there anyway to reinstall the default mac boot loader without reinstalling the OS? 

Thanks for any help and insight you can offer into this strange and mysterious process.

---

### Post by Rxke on 2006-04-22
I'm typing this on a laptop w/ a broken screen and crappy keyboard, so don't be upset when i'm a bit telex-esque in my descriptions ;)

The file youo want is /etc/yaboot.conf
info about it you can find /usr/share/doc/yaboot/yaboot-howto.html
and some examples  /usr/share/doc/yaboot/examples

i guess all you have to do is change the timeout=100 to 30 (tenths of seconds)
and put the entry that sez macosx=/dev/hda3 (or wherever it resides before the boot=/dev/hda2 (again: depends on yr system, cld be hdb9 etc...) entry.

hope it helps

---

### Post by CSMatt on 2006-04-22
[QUOTE=MechaShiva]I have a similar question and figure it's better to post it here than on a new thread.  I have a pmac g5 that I would like to dual boot with linux.  I'm a long time linux user but I've never used it on ppc before.  So my question is, where is the boot loader written?  Is it written to the hard drive or is it some openfirmware voodoo?  

Here's the full scenario: I have a test hard drive that I would like to set up with linux to make sure my hardware works as expected but I don't want to resize/repartition my primary drive.  So my plan is to swap out my primary, throw in a spare hard drive and install it on there.  If it works as expected, I'll slave the test drive and dual boot it that way.  My concern is if the bootloader is written to openfirmware, when I put my primary drive back in, will it boot properly?  Or is the boot loader written to the hard drive in which case once I pull the drive out, no harm no foul.  

Also, if I pull the spare drive out, is there anyway to reinstall the default mac boot loader without reinstalling the OS?

Thanks for any help and insight you can offer into this strange and mysterious process.[/QUOTE]
This I can actually answer.

The bootloader probably goes on the first partition on the drive, called the "Apple Bootstrap."  The bootstrap is about 128 MB in size and contains all necessary boot information for that drive.  I'm pretty sure of this because when I completely cleared out my hard drive and installed Mandriva the iBook would only display the folder with the question mark upon reboot.  This being said, you can probably install Linux on your second drive and the bootloader will be written onto that drive while still detecting Mac OS X on the first drive and installing it as an option.  However, I would first partition the second drive with Disk Utility as it is the only partitioner that I know of that puts the bootstrap partition in if it isn't already there.  Use Disk Utility to create a "dummy" partition to fill the entire drive (the bootstrap partition is made automatically and without your consent as to size) and use the partitioner that came with your Linux distribution to delete it.  However, if you remove your Linux drive, OpenFirmware may not be able to find the operating system for the Mac OS X drive.  If this happens, hold down the option key after the fanfare sound and a list of all bootable partitions will be presented to you after about three minutes of searching all possible outputs.  The Mac OS X partition will have a small "X" in the bottom right corner.

Personally, I like the BIOS system better.

---

### Post by CSMatt on 2006-04-23
.

---

