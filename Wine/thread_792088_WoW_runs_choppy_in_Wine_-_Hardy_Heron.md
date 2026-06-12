---
title: "WoW runs choppy in Wine - Hardy Heron"
date: 2008-05-12
forum: Wine
---

### Post by kc5hwb on 2008-05-12
[http://ubuntuforums.org/showthread.php?t=742227](http://ubuntuforums.org/showthread.php?t=742227)

I had this thread going with Fiesty and it was determined that my video driver wasn't correct.  I ended up going back with XP for a short time, but now that Hardy is out, I decided to switch back to Linux.. thank GOD.

I did a fresh install of 8.04 and everything detected perfectly.  I   ran all the updates from Update Manger, installed Wine, and then installed WoW from this link:
[http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)

In addition to the REGEDIT config at the bottom, I opened up the config.WTF file and added these 2 lines:

```
SET ffxDeath "0"
SET ffxGlow "0"
```

However, the video is still choppy.  IT DOES WORK, so that is an improvement over running it in Fiesty on this laptop, but the video is so choppy that I don't really want to play it yet on this box.

My laptop is this one:
[http://www-307.ibm.com/pc/support/site.wss/quickPath.do?quickPathEntry=2529R5U](http://www-307.ibm.com/pc/support/site.wss/quickPath.do?quickPathEntry=2529R5U)

My video card is this one:
Mobile 915GM/GMS/910GML Express Graphics Controller

---

### Post by kindofabuzz on 2008-05-12
try -opengl

---

### Post by kc5hwb on 2008-05-12
try that where?

---

### Post by kc5hwb on 2008-05-12
ok, I tried that behind the .exe file from Terminal by running:

```
wine "C:\Program Files\World of Warcraft\WoW.exe" -opengl
```

That doesn't improve performance any, it is still choppy

---

### Post by VampiricFang on 2008-05-12
> **kc5hwb said:**
> ok, I tried that behind the .exe file from Terminal by running:

```
wine "C:\Program Files\World of Warcraft\WoW.exe" -opengl
```

That doesn't improve performance any, it is still choppy

Is your graphics card Linux compatible? That could be an issue too.

---

### Post by Faud on 2008-05-12
Its the graphics card. There are threads in here that are just for that card. The drivers for linux are far, far from par.

---

### Post by thisismalhotra on 2008-05-13
> **kc5hwb said:**
> [http://ubuntuforums.org/showthread.php?t=742227](http://ubuntuforums.org/showthread.php?t=742227)

I had this thread going with Fiesty and it was determined that my video driver wasn't correct.  I ended up going back with XP for a short time, but now that Hardy is out, I decided to switch back to Linux.. thank GOD.

I did a fresh install of 8.04 and everything detected perfectly.  I   ran all the updates from Update Manger, installed Wine, and then installed WoW from this link:
[http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)

In addition to the REGEDIT config at the bottom, I opened up the config.WTF file and added these 2 lines:

```
SET ffxDeath "0"
SET ffxGlow "0"
```


However, the video is still choppy.  IT DOES WORK, so that is an improvement over running it in Fiesty on this laptop, but the video is so choppy that I don't really want to play it yet on this box.

My laptop is this one:
[http://www-307.ibm.com/pc/support/site.wss/quickPath.do?quickPathEntry=2529R5U](http://www-307.ibm.com/pc/support/site.wss/quickPath.do?quickPathEntry=2529R5U)

My video card is this one:
Mobile 915GM/GMS/910GML Express Graphics Controller


Try this thread and pages on Ubuntu support (this links are inside the thread)



[http://ubuntuforums.org/showthread.php?t=770939](http://ubuntuforums.org/showthread.php?t=770939)

---

### Post by kc5hwb on 2008-05-13
Malhotra,
I read through that entire thread just now and don't really see the problem that I am having, along with my video card.  I do see some similar issues, but those people are all running other cards.

Faud,
I assume you mean that the drivers from Linux are below par, since the graphics card itself ran WoW just fine when I had XP installed on this same laptop.  I will search for some better linux drivers for this card here.

---

### Post by kc5hwb on 2008-05-13
After some more reading, I uninstalled compiz (no idea what this prog does) and I added this link to my config.wtf file:

SET M2UseShaders "0"

Now the game runs MUCH smoother... at least at the login screen.  I  am at work right now and cannot connect to the server from here, but from what I can see this might have solved my problem.  I will update this thread again later today when I get home. (or to the bar with free wifi)

---

### Post by kc5hwb on 2008-05-13
ok, I just played for about 10 min and the video is much smoother, but some things still don't appear correctly.  For instance, my buttons on my bars are very pixelated so I can't see what they are, same thing on my bags.  Also, sometimes when I run around, the sky or the ground will appear solid white or black.  This is obviously a graphics card issue, but I know that the card will run the game because it worked perfectly in XP.

---

### Post by Zypher on 2008-05-13
[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

Is a very good source for information.

---

### Post by MemoryDump on 2008-05-14
something has obviously been changed in the recent Wine releases to cause this from happening. Other than upgrading Wine (through the repos) I haven't changed a single setting on my system. WoW worked flawlessly in the past. There wasn't any mouse lag, no pixalation or lag period in the game.

Hopefully this (and probably many other bugs/issues) will be resolved before Wine 1.0 is official released.

---

### Post by Rudedawg on 2008-05-14
I think this might be a graphics card driver issue. Even in XP, 90% of Intel's on-board graphic cards had to have a driver update in order to run wow smoothly. Vista wasn't any better.

I am very interested in this thread since I'll be installing wow via wine once I get my wireless card and graphics card working properly.

---

### Post by kc5hwb on 2008-05-14
> **Rudedawg said:**
> I think this might be a graphics card driver issue. Even in XP, 90% of Intel's on-board graphic cards had to have a driver update in order to run wow smoothly. Vista wasn't any better.

I am very interested in this thread since I'll be installing wow via wine once I get my wireless card and graphics card working properly.

This is obviously a graphics driver issue.  That I knew.  But from what I have read on this board, no one makes a good linux driver for this vid card, and I was hoping to find some way around it, or some tweak that would make it work better

---

### Post by kc5hwb on 2008-05-14
Also... I just looked... I have Wine 1.0 rc1 installed.

---

### Post by kc5hwb on 2008-05-14
From [http://www.wowwiki.com/Linux/Wine/Troubleshooting](http://www.wowwiki.com/Linux/Wine/Troubleshooting)

I set this line in the WTF file


```
Set UIFaster "2"
```

However, my bag icons still do not appear correctly

---

### Post by Zypher on 2008-05-14
One thing I really like to do.

```
env WINEPREFIX="/home/<user>/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe" -OpenGL -console
```

That would be how I launch World of Warcraft.

With that you have a couple options you can run in game via the Developer Console. Almost all graphic settings that ask you to restart the game can be done with

```
gxRestart
```

All settings that can be changed from the Config.wtf file can all be edited here.

gxApi OpenGL or Direct3D

---

### Post by kc5hwb on 2008-05-30
I SWEAR that I saw an article on this forum a few weeks ago about an ACTUAL release of WoW from Blizzard for Linux... but now I can't find it.  Was I wrong?  Has anyone else seen this?  I read on it about a release date of this July for a Linux version of WoW.

---

### Post by MemoryDump on 2008-05-30
> **kc5hwb said:**
> I SWEAR that I saw an article on this forum a few weeks ago about an ACTUAL release of WoW from Blizzard for Linux... but now I can't find it.  Was I wrong?  Has anyone else seen this?  I read on it about a release date of this July for a Linux version of WoW.

I'll believe that when I see it, have it installed and I'm running it :P
would be awesome if they did.. but it's very unlikely. :(

---

