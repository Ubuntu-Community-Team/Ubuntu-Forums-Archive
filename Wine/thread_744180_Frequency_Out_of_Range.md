---
title: "Frequency Out of Range"
date: 2008-04-03
forum: Wine
---

### Post by iheartubuntu on 2008-04-03
Trying to play a windoze based game through Wine, but when the game starts up, the frequency of my monitor changes and goes black. Is there any setting in Wine I can do specifically for this game only? If so, how do I set it up. Thanks!

---

### Post by iheartubuntu on 2008-04-28
Any tips on this? I cant seem to figure it out :| Thanks for any ideas!

---

### Post by CarpKing on 2008-04-28
It sounds like the game is changing your screen resolution, color depth, or refresh rate to something that your monitor doesn't like.  I'm not really sure how to remedy it though.  Maybe making sure that whatever it is is listed as a modeline in xorg.conf will help; I don't know how that all works.  Do you have any way of changing the game's resolution without running it?  You could set it to your monitor's.

Actually, another thought.  Have you tried setting Wine to use a virtual desktop?  This is a global setting, but if it works you can set Wine to use a different wineprefix (the typical one being ~/wine) for only that program.  I don't know how to do it but it's probably in one of the stickies.

---

### Post by iheartubuntu on 2008-06-23
> **CarpKing said:**
> It sounds like the game is changing your screen resolution, color depth, or refresh rate to something that your monitor doesn't like.  I'm not really sure how to remedy it though.  Maybe making sure that whatever it is is listed as a modeline in xorg.conf will help; I don't know how that all works.  Do you have any way of changing the game's resolution without running it?  You could set it to your monitor's.

Actually, another thought.  Have you tried setting Wine to use a virtual desktop?  This is a global setting, but if it works you can set Wine to use a different wineprefix (the typical one being ~/wine) for only that program.  I don't know how to do it but it's probably in one of the stickies.

Finally had time to check this... I configured WINE to run as a virtual desktop and it runs the games just fine! Thanks!

---

