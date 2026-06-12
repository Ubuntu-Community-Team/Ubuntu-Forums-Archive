---
title: "32 to 64 w/Separate Home Partition"
date: 2006-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by ogregore on 2006-08-12
Hey all,

I have been running 32 bit from breezy to dapper on an Averatec 6240 lappy which has the AMD 64 mobile Athlon 3200 chip. I have a separate / and /home partition and a separate ntfs partition. 

My question is: If I install 64 bit dapper on the / partition am I going to have to also clean out or recreate my /home partition? I don't want to bung up the new install with all the settings that would be left over for FF, TB etc in my home partition.

I thought I would ask this time as my policies in the past have usually been "do the new install/update, curse my inpatience, google/search ubuntu forums, repeat step one."   [-o<

Cheers
Ogre

---

### Post by finite9 on 2006-08-23
If you leave your home partition it *will* try to use current configuration when you install 64bit.  It's only config files in /home so it's not architecture specific.  But if you're going to install the same apps. does it really matter if you leave /home as it is?

If it does matter, then simply, view hidden files and delete the .<folders> that contain config for apps you don't want on the new system.

---

### Post by ogregore on 2006-08-23
Thanks, still not sure if I'm ready to move to 64 bit, but now I know what to expect.

Cheers
Ogre

---

