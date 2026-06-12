---
title: "WoW sign in issue under wine"
date: 2007-08-26
forum: Wine
---

### Post by boolean10 on 2007-08-26
My problem appears to have started after installing the latest version of wine(0.9.44). When i go to launch WoW it stop at the sign in screen... Has anyone else seen this

The wine version is: wine-0.9.44
Ubuntu version is : Ubuntu 7.04 - the Feisty Fawn
System : Intel Core 2 Duo 2.13GHz, 1Gb ram
Video Card : Nvidia GeForce 7600 GS
Wine Config : XP

It you need any more information Please let me know
And thank in advance for any help

---

### Post by graigsmith on 2007-08-26
revert to an older version of wine, the regular one in the repository works fine.

---

### Post by Nehvrook on 2007-08-26
I'm having the same problem. Is there not another way to fix it that going back a version? What's caused it?

EDIT, forget that. Totally wierd but if you delete the WTF folder in the WoW directory it'll fix it. You can even delete the WTF, run the game, close the game and put your original WTF back and it'll work. No idea what's gone on here lol

---

### Post by boolean10 on 2007-08-26
Cool thanks i'm going to try that now! Cause i really didn't want to revert... no offenses but it seems a little counter-progressive.

---

### Post by boolean10 on 2007-08-26
Hmm... that didn't work either, it still pauses at the same dialog "Downloading"

---

### Post by Nehvrook on 2007-08-26
Strange. Mine was pausing at downloading too. But deleting the WTF fixed it. You might have to use synaptic to force and the last version of wine untill this is fixed.
But doing the WTF worked for me on two seperate PC's so I don't get it

---

### Post by mccord on 2007-08-26
had the 'stuck at downloading' problem last week
starting the game in d3d mode once (remove 'SET gxApi "opengl"' from config.wtf) fixed the issue
after that i could use opengl mode again :)

---

### Post by boolean10 on 2007-08-26
Thanks a million mccord... that did the trick, although still very strange it would do that.

---

### Post by Nehvrook on 2007-08-27
That's essentially what I did as well. I just removed the whole config rather than finding the specific thing that was causing it. I did suspect it was a problem with loading in opengl from the stuff the terminal spewed out on crash.

Are you guys still getting a crash when you try to close the game though?

---

### Post by Naegling23 on 2007-08-27
I had this problem yester day as well.  I found a topic discussing this on the WoW forums(sorry, I cant link it, the site is banned here at work), so here is the result:

When you try to log into the game, blizzard is trying to gather some player information, which it usually doesnt do.  When it gets to the downloading part of login, wine choaks on the uploading of the info in open-gl mode, and the game freezes.

My solution was to cd into my wow folder, and launch WoW directly, instead of the -opengl option that is contained in my (and most other peoples) login script.  What this means is that you need to run WoW.exe instead of WoW.exe -opengl.  I successfully logged in using this, it transferred the informantion to blizzard, and I logged back off, and started the game normally (with the -opengl option).  It all works now.

The d3d option works because your not running the game in opengl mode, which is important for some reason.

Hope this clears it up, and solves the problem for everyone!

---

