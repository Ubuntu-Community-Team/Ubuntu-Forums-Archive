---
title: "Running Nexuiz at 280FPS but Wine Games only ~30FPS?"
date: 2013-08-18
forum: Wine
---

### Post by Thee on 2013-08-18
So while I was trying to figure out why on lowest settings of WoW and GW2 running under WINE, I'm getting max 30 FPS, which drops as low as 10 FPS, I installed Nexuiz just to compare, to make sure that everything works with native games, and I discovered that on Max settings I'm getting up to 280 FPS and rarely a minimum of 80 FPS while running Nexuiz.

I have the latest stable proprietary drivers installed, I tried changing CPU mode from Ondemand to Performance, I even tried running GW2 on a separate X server, and the FPS remains relatively the same...

Could it really be that WINE has such a big impact on performance? I mean, that's 10 times lower...

---

### Post by A Bunny on 2013-08-19
You could try running your wine games under play on linux. Link [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/) . This should help improve performance.

Hope this helps.

---

### Post by Thee on 2013-08-19
Thanks, but I tried that too. It's more or less the same :/

---

### Post by zteam2 on 2013-08-23
Try different versions of wine, and you can also play around, with the wine settings.

---

### Post by A Bunny on 2013-08-24
Try this link then [http://appdb.winehq.org/objectManager.php?sClass=version&iId=26558](http://appdb.winehq.org/objectManager.php?sClass=version&iId=26558) .

Hope this helps.

---

### Post by Thee on 2013-08-25
I've tried multiple versions of Wine using Playonlinux and performance is the same or it doesn't run at all.
I've also read the Wine GW page several times and tried various suggestions there, and nothing seems to improve the FPS.

What troubles me is that 25-30 FPS would be acceptable if it was stable, but just on camera move it jumps down to ~10 or freezes the game for a second or two, which really makes it unplayable.

---

### Post by Tweak42 on 2013-09-03
> **Thee said:**
> I've tried multiple versions of Wine using Playonlinux and performance is the same or it doesn't run at all.
I've also read the Wine GW page several times and tried various suggestions there, and nothing seems to improve the FPS.

What troubles me is that 25-30 FPS would be acceptable if it was stable, but just on camera move it jumps down to ~10 or freezes the game for a second or two, which really makes it unplayable.

I can say that the weaker area of wine is in doing the 3d translations (there's alot of stuff going on in the background that its a miracle that it even works at all), and that there is lack of support on the multi core processor front.  Games that make use heavy use of multi core cpu are affected quite negatively unfortunatly.  Wine development tends to put priority on getting stuff to work and performance is secondary.  

There are a few patches that are working toward performance, but no complete solution yet.  See this thread: [http://bugs.winehq.org/show_bug.cgi?id=11674](http://bugs.winehq.org/show_bug.cgi?id=11674)  The latest experimental patch (by a codeweaver developer no less!) is showing promise.

---

