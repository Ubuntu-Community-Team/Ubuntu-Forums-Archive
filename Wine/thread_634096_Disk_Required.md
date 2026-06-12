---
title: "Disk Required"
date: 2007-12-07
forum: Wine
---

### Post by nickej on 2007-12-07
I'm trying to run Crimson Skies under WINE/Gutsy, and while it installed fine,the game has a "security" feature that requires me to have the disk in the drive when it launches. Unfortunately, WINE (or Gutsy, I dunno) can't tell the disk is in, so I get the "Please insert the proper disk, Press 'OK' and restart". I'm pretty new with Ubuntu, but I'm assuming I can get it to work with some startup arguments appended somewhere, but I have no idea where to begin looking....Any advice much appreciated.

---

### Post by cogadh on 2007-12-07
Wine does not have complete support for all game copy protection schemes yet. If the game is SceuROM protected, then it will likely detect the disk correctly, if Wine is configured correctly:[LIST=1]
[*]Make sure that you have your CD-ROM drive configured as type "CD-ROM" in winecfg
[*]Create a symbolic link to your CD-ROM drive's /dev entry in Wine's dosdevices directory:
```
ln -s /dev/hdc ~/.wine/dosdevices/d\:\:
```
The above assumes that you have your CD-ROM drive set up as "D:" in Wine and that Linux has it as /dev/hdc. Change the above to reflect your actual Wine and sytem config
[/LIST]
If that does not work, then it is likely that the game is not using SecuROM and has some other copy protection scheme that does not work in Wine. The only way you will get the game to work is with a "no-CD" cracked executable. Do not ask how to get or use one on these forums. Since cracks are often used to pirate software, the discussion of the how's and why's of cracks is strongly discouraged. Google is your friend, use it.

---

