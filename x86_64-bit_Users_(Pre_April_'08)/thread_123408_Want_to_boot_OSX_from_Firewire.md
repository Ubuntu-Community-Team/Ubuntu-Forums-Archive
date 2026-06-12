---
title: "Want to boot OSX from Firewire"
date: 2006-01-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by burobaaje on 2006-01-30
I have OSX 10.3 and ubuntu on the internal drive of an iMac and OSX 10.4 on a firewire drive.  yaboot allows me to boot both of the OS's from the internal drive, but as most know if I use System Preferences to boot the external drive, yaboot goes away.  It can be replaced easily by using ybin...

But...I would like to set up yaboot to be able to select all three so as to never have to use System Preferences to get to the firewire OSX.  Using mac-fdisk I think the firewire drive is /dev/sd3, but when I try to put that into the yaboot.conf, ybin fails to upgrade.

Anyone know how this can be done?  Maybe I don't know what the actual device name is for the firewire drive and may not know how to put it into yboot.conf properly.

Any help appreciated.

---

### Post by sonofcolin on 2006-01-30
Can you not hold down the option key during boot? If the FW drive is attached you should then be given the option to boot from it.

---

### Post by burobaaje on 2006-01-30
Thanks, holding down the option key works, but it would be nice and simple to get both of the OSX's into the yaboot menu.  Wonder if that can be done?

---

### Post by burobaaje on 2006-01-30
Though holding down the option key while booting gets me into a Firewire drive's OSX, I would like to know how to add this option to yaboot's menu.  I have used mac-fdisk -l to get the firewire drive's dev and have added it, but evidently that was not it.  Anyone know how?

---

