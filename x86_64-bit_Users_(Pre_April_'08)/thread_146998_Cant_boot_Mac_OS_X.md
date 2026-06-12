---
title: "Cant boot Mac OS X"
date: 2006-03-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by hubs1b on 2006-03-19
Installed ubuntu on my iMac G5, during installation, I had two partitions 1 with mac osx (50gb) on it and one that was free space formatted as hfs extended (25gb). I selected 'manually edit the partition table' and selected the free space partition for the use of ubuntu. I then formatted that partition to install ubuntu on it. The partition table then showed the change: 

-Boot partition for macosx  
-macosx
- 3 partitions for ubuntu (one of them being the main boot partition.)
 
Then ubuntu installed and reboot. When I came back to boot up macosx again I get a grey screen with a circle and line through it, assuming it cant find macosx boot partition. Does this mean that I have lost my macosx partition completely as ubuntu (installation Cd) only shows the one partition of 75 gb when I look at the partition table ? 

Also when booting up ubuntu, at the login screen I lose the functionality of the Keyboard and Mouse ?

---

### Post by grazie on 2006-03-19
I've never been near a G5 so don't know if I can offer much help, but here goes.

Any particular reason for doing a manual edit on there partition table? Ubuntu does a reasonable job on auto detect. If you don't quite like what it's done you can always fine tune before accepting. It also gets the flags and mounts points right!

When the partition table edit is complete, for your basic dual boot installation you should have seen the following partitions (although the installer doesn't name them IIRC)

bootstrap
MacOSX
Ubuntu (root)
Swap (Linux)

The PPC architecture doesn't need a boot partition, so one shouldn't have been created. OSX and Linux are booted from the bootstrap partition.

From your description it does sound like you've lost OSX. You could use parted to create space for OSX again, but you'd be wasting time since AFAIK you can't yet create HFS+ partitions from Linux and OSX can only partition whole disks. Sorry!

No idea with the keyboard and mouse.

---

### Post by tidris on 2006-03-19
[QUOTE=hubs1b]When I came back to boot up macosx again I get a grey screen with a circle and line through it, assuming it cant find macosx boot partition.[/QUOTE]
What happens if you hold down the Option key after rebooting? How many icons do you see in the OpenFirmware boot screen and what OSes are they for?

---

### Post by AlphaMack on 2006-03-20
You more than likely fubared your OS X install.

I suggest following [these directions](http://members.cox.net/kadymae/dualboot.html).  The key is to use Disk Utility to format your Ubuntu partition as free space then let the Ubuntu installer do its magic.

---

