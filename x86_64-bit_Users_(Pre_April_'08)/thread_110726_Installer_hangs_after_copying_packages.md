---
title: "Installer hangs after copying packages"
date: 2005-12-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rovenhot on 2005-12-31
Dual 500Mhz G4, installing Breezy PPC onto a 9 GB partition of a LaCie 40 GB portable external hard drive via Firewire.

The installation goes smoothly after fiddling with the partition table, but after the base system and packages are installed, the installer freezes (I am assuming this after 20~30 min. of inactivity).  Screen shows only the installer background color (red), no signs of activity from hard drive or elsewhere.

I reboot and hold <opt> to bring up the boot device screen, but the partiton doesn't show up, thus it is not recognized as bootable.  What else is there to install in order to make it so?

I'll try reinstalling now.

---

### Post by Rovenhot on 2005-12-31
Ah ha...I didn't configure the network (too lazy to find the wireless network key).  Could it have been trying to update packages?  I'm not familiar with the Ubuntu installation process, but I seem to recall that an internet connection was required.  I'll try that...

If anyone knows whether what I'm doing is the right thing, please tell me.

---

### Post by Rovenhot on 2005-12-31
Trying "expert" mode...

Network was configured without problems, but still hung after the packages were copied.  Pressed CTRL-C and got back to the menu, and found out that the faulty step in the process was configuring the time zone.  I skipped it, and proceeded to the installation of yaboot onto the bootstrap partition.  A dialog told me almost immediatly that the installation of yaboot failed, but allowed me to continue.  Then, at 50% progress, it hung while "looking for other operating systems."  I restarted, but I still can't boot from my 9 GB partition.

---

