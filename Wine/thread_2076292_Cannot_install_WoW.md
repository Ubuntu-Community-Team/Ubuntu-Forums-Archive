---
title: "Cannot install WoW"
date: 2012-10-25
forum: Wine
---

### Post by ConfusedWoW on 2012-10-25
I've been spending awhile trying to install WoW fresh.  I only have Linux installed on this PC, and have no other WoW install.  I can't for the life of me get the installer from the web to run.  Here is what happens:

I run wine World-of-Warcraft-Setup-enGB.exe

I then get a window that pops up "World of Warcraft Setup"

'Failed to run a required program (Blizzard Setup).  Wait one minute and try again and if that doesn't work please restart your computer and try again.  

Error code:  BLZPTS0000 | '

And here is the terminal output:

Unable to read archive hash table: "C:\users\Public\Application Data\Battle.net\Setup\wow_engb\SetupWin.mpq"

Here are some details of my system:

Ubuntu 12.10 64bit
Intel Q6600 quad core
Wine 1.5.15
Installer downloaded from battle.net today

I combed through the FAQs and forums and web, and I can't find anyone with this problem either.  The problem seems to be with graphics, crashing, or getting the program running well, not with failure at installation....  

any ideas?

---

### Post by ConfusedWoW on 2012-10-25
By the way, I've tried with wine 1.4 as well to no avail.

---

### Post by Tweak42 on 2012-10-29
Have you tried installing from a clean wineprefix?  I'm not sure if it's required for a download install, but IE7 and/or some other DLL components might also be needed for the downloader to work.

Rename or delete the .wine directory in your home directory (you need to show hidden files in Nautilus to see it).  Then run winecfg to recreate the new prefix, and possibly change the windows version to XP.  Then run winetricks to install IE7.

If all else fails you can grab a copy of wow from a windows install, just run the launcher.exe first so it can update and verify the game files.

---

### Post by irzan2010 on 2012-11-01
Hi,
Maybe you can try this installer : [http://www.indogamers.com/page/wow/](http://www.indogamers.com/page/wow/)
I have try this installer and I can install and run WOW

---

