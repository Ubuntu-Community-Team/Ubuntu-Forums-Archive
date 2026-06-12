---
title: "Diablo 2 Expansion"
date: 2012-04-23
forum: Wine
---

### Post by N64Cam on 2012-04-23
I have wine 1.2, Im trying to install the program i press install.exe inside the cdrom and it is not executable so i open up properties click allow executing file as program but i get this error sorry could not change the permissions of ''install.exe'':error setting permissions:Reading-only file system
Please help me install.

---

### Post by N64Cam on 2012-04-23
please help me install.. i really want this  game.

---

### Post by oldos2er on 2012-04-24
Moved to Wine. Please don't bump your thread more than once every 24 hours.

---

### Post by donkyhotay on 2012-04-24
It sounds you're trying to run it natively, not in wine. This usually happens if you just double-click on the file. Try opening it with wine instead.

---

### Post by N64Cam on 2012-04-24
The file '/media/EXPANSION/install.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

---

### Post by ccornchip on 2012-04-27
Unlike the OP, I have managed to install D2X on my fresh installation of ubuntu 12.04 LTS (precise), but I have a problem.

First thing's first @OP this is how I did it, hopefully it'll work for you too.
- click on the CD icon to open a navigator-thing (what's-it-called? files? dolphin?)
- Right-click on INSTALL.EXE then "Open With Wine Windows Program Loader"
... at least that's how I got it to work.


--- Now my problem ---
It's installed, I even installed the expansion, did the graphics test and everything.
There is no desktop icon to speak of, so I can navigate my way to the LOD CD right-click INSTALL.EXE the open with wine ...
it starts, the little splash-screen comes up, I click on "Play Diablo II : Lord of Destruction" the box closes and ... nothing.

Opening up a terminal, I notice that when I do "top", Game.exe is there happily consuming 100% of CPU ... but no game to interact with.

Any ideas?
winecfg seems to be different to what it was when I was in 11.10 (where it was working). I'm using wine-1.4

--edit:
oooh! I just noticed that when I kill the application, a window pops up telling me to verify that my D2X:LoD is in my CD-ROM drive (retry:cancel)
winecfg has /media/Expansion in the drive mappings ... so, perhaps it's copy-protection??

--edit (again) :
omg, omg, omg, I got it working!
I downloaded the patch from [http://us.battle.net/support/en/article/diablo-ii-patch-information](http://us.battle.net/support/en/article/diablo-ii-patch-information)
then ran it (again through wine) and the game now works!

@OP, I'm happy to help you if you're still having troubles.

---

