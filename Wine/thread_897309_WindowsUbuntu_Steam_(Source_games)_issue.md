---
title: "Windows/Ubuntu Steam (Source games) issue"
date: 2008-08-22
forum: Wine
---

### Post by snarebear on 2008-08-22
I would like to conserve space on my drive by having Steam accessible from both Windows and Ubuntu. I am successfully able to play CS:S in Ubuntu but I am unable to load it at all in Windows; Team Fortress 2 works in both. When I try to load CS:S in Windows, I get the "blank screen" that many people get with Wine. I then tried to install CS:S within my Windows partition and it works flawlessly. I have tried reinstalling Steam from Wine, recovering my Windows partition, and also copied over the Steam folder from Windows to Ubuntu; none of which worked. If this is a problem I have to live with, I guess I'll will be buying a larger drive. If anyone has any fixes, I would greatly appreciate it.

Compaq Presario V6000
Ubuntu 8.04
Windows Vista
Wine 1.1.2
Ext2 IFS 1.11
nVidia GeForce 6150

---

### Post by lswest on 2008-08-22
> **snarebear said:**
> I would like to conserve space on my drive by having Steam accessible from both Windows and Ubuntu. I am successfully able to play CS:S in Ubuntu but I am unable to load it at all in Windows; Team Fortress 2 works in both. When I try to load CS:S in Windows, I get the "blank screen" that many people get with Wine. I then tried to install CS:S within my Windows partition and it works flawlessly. I have tried reinstalling Steam from Wine, recovering my Windows partition, and also copied over the Steam folder from Windows to Ubuntu; none of which worked. If this is a problem I have to live with, I guess I'll will be buying a larger drive. If anyone has any fixes, I would greatly appreciate it.

Compaq Presario V6000
Ubuntu 8.04
Windows Vista
Wine 1.1.2
Ext2 IFS 1.11
nVidia GeForce 6150

It might work best if you save the game files on a seperate  fat32 partition (shared space).  I think the problem is coming from the fact that Windows does not natively read or write to ext3 systems.  You could always just make it /media/storage, then copy the game files over, or set the mountpoint to be /home/username/.wine/drive_c/ if you really wanted to.  I'm not sure, it's just my opinion.

---

