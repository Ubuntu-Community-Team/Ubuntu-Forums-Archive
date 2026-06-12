---
title: "Windows game cant find my CD-ROM"
date: 2016-04-26
forum: Wine
---

### Post by john547 on 2016-04-26
I installed a game called Warbreeds via playonlinux/wine1,5 and now I am trying to run it the executable ceated after the installation works but ingame an error message pops asking me to put on the CD-ROM of the game first in order to be able to play it.

I have the original CD in my real physical drive (/dev/sd0)

on winecfg under "drives" tab I see this:

Letter: D || Target forlder: /media/cdrom

and some other drives such as /drive_c etc

under that (while having selected the drive with letter D) I see:

Path: /media/cdrom || Type: CD-ROM || Device: /dev/sr0 (<- so this should be a good sign since the original physica disk is inserted on that device ) || Label: WARBREEDS || Serial 7708C34E (just out of curiosity what is that? and where does it refere to? is it for example the serial number of my drive or the serial of the disk inside it? ) 


Please help me :)

---

### Post by yoshii on 2016-04-26
I think in Wine Configuration (winecfg), your Windows D:\ drive needs to be set to path:  "/cdrom".  
Putting it into "/media/cdrom" is incorrect.  Also the type needs to be set as CD-ROM which is visible if you show the advanced settings.  
Make sure you restart your system after saving the changes.  

I hope this helps.

---

### Post by john547 on 2016-04-30
there is no such a path it doesnt even "see" my cdrom that way the proper folder is either /dev/sr0 or /media/cdrom/

---

