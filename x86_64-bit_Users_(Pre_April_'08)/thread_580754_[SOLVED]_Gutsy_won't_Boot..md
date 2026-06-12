---
title: "[SOLVED] Gutsy won't Boot."
date: 2007-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-10-19
Okay, here we go again.  I downloaded the GutsyLive ISO and it boots to the 1st menu.  When selecting option 1 to boot/install from livecd, I get the kernel progress bar, some information about kernel live at the bottom of the screen, then it all goes blank and keyboard lights flash.

I assume it's the usual ATI suspects and do my normal work around (that I used for 7.04).  I hit F6 and change the resolution to 640x480 and same thing happens.  I select safe graphics mode and no change.

My checksum as follows: 
md5sum ubuntu-7.10-desktop-amd64.iso
61c87943a92bc7bf519da4e2555d6e86  ubuntu-7.10-desktop-amd64.iso

I can't find a checksum to compare it to, so I don't know if it's good.  Even using the menu option to check the CD it loads kernel and then goes through the whole blank screen thing.

Any suggestions I can try?

---

### Post by crjackson on 2007-10-19
Okay, got it to work.  It has graphics problems solved by F6 and removing the word splash as well as removing quite.

Next it was burned on bad media.  I reburned and made the above changes.  Booted to desktop.  On for 5 minutes and already like it better than 7.04.

---

### Post by Skweek on 2007-10-19
Hiya, this might sound crazy, but it worked for me. Just Google the checksum!!

---

