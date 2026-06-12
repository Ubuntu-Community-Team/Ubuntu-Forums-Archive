---
title: "WoW error #121"
date: 2008-09-27
forum: Wine
---

### Post by Greyed on 2008-09-27
This is getting frustrating.  I copied my WoW installation over from my NTFS partition onto my ext3 partition and ran it in wine.  I've done this in the past but recently it has constantly been throwing an error #121 at me.

According to Blizzard that is data corruption of the game files.  Their solution is to run the repair tool.  I have done that, several times, didn't help.  So I just copied all the files over again.  First run, again, error #121.  

What is frustrating is I know the files aren't correupted.  Reboot into WinXP, WoW runs fine every time.  If the files were corrupted that would not be the case.

Anyone hit this conundrum and, if so, devised a workaround?  Preferably something that doesn't involve the slaughter of goats or chickens.

---

### Post by asdfoo on 2008-09-28
> **Greyed said:**
> This is getting frustrating.  I copied my WoW installation over from my NTFS partition onto my ext3 partition and ran it in wine.  I've done this in the past but recently it has constantly been throwing an error #121 at me.

According to Blizzard that is data corruption of the game files.  Their solution is to run the repair tool.  I have done that, several times, didn't help.  So I just copied all the files over again.  First run, again, error #121.  

What is frustrating is I know the files aren't correupted.  Reboot into WinXP, WoW runs fine every time.  If the files were corrupted that would not be the case.

Anyone hit this conundrum and, if so, devised a workaround?  Preferably something that doesn't involve the slaughter of goats or chickens.

forgive my ignorance, but what's wrong with installing from scratch?

---

### Post by Greyed on 2008-09-28
> **asdfoo said:**
> forgive my ignorance, but what's wrong with installing from scratch?

2+ years of patches as well as I am a heavy user of addons.

---

### Post by Espryon on 2008-09-28
> **asdfoo said:**
> forgive my ignorance, but what's wrong with installing from scratch?

I 2nd reinstalling it

---

### Post by Eviljim on 2008-09-29
a) Can you get into the game before it crashes? 
or 
b) Does it crash upon start up?

If a) is true then logout and disable all addons and enter the game. If this works, you need to root out the offending mod. I would start with Cartographer, as this causes my WoW to bomb out to the desktop.

If b) is true, has the WoW install folder still got write permissions? This would be required for the WTF folder at least, as it updates the config.wtf file as well as all the mod .lua files within the WTF folder. If WoW cannot write these files it could generate the error message, as it would think that the folder is corrupt?

---

### Post by Greyed on 2008-09-29
> **Eviljim said:**
> a) Can you get into the game before it crashes? 
or 
b) Does it crash upon start up?


No and Yes.

> If b) is true, has the WoW install folder still got write permissions? This would be required for the WTF folder at least, as it updates the config.wtf file as well as all the mod .lua files within the WTF folder. If WoW cannot write these files it could generate the error message, as it would think that the folder is corrupt?

The folders are writable.  :(

---

### Post by Greyed on 2008-09-29
Well, deleted the directory on the ext3 partition, copied everything over again and, TADAAAAA, it worked.  No idea what changed between this copy and the last.  Had to spend another 20m banging my head against the wall at it dying when starting up.  Then it dawned on me, I was using nvidia-glx-new which has never worked for gaming.  Backed out to good ol' nvidia-glx and it fired up first time.  Works in full screen, too.  :D

---

