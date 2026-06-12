---
title: "Recurring problem installing Civilization IV from single DVDROM"
date: 2012-08-08
forum: Wine
---

### Post by finrod_felagund on 2012-08-08
I've looked for this here, and elsewhere, but cannot seem to find a match.

I'm trying to install Civ IV on 10.04 Lucid.  I have tried using both the manual and wizard methods in PlayOnLinux (and also tried Winetricks (using Ubuntu 11.04).

Using all three approaches above, installation appears to go smoothly, until a point about 75-80% into the progress bar, when it prompts for the second disk on drive D: - but I'm loading from a single CD ROM.  I've tried just clicking on the Forward box, and putting in a blank CD-RW to no avail.

Installation always seems to abort at the same point,

I've also tried using wine from the terminal prompt, without success. I can't seem to navigate to the SETUP.exe file.

Thanks for reading.

Mark

---

### Post by Sunships on 2012-08-12
It's probably that the PlayOnLinux script was written to handle an installation from a version with multiple CDs, so won't work for a single disk installation.

Try installing Wine, and using that to run setup.exe - that worked for me.

---

