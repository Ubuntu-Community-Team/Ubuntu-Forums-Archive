---
title: "Warcraft 3 Working But Weird Problem Encountered"
date: 2008-04-22
forum: Wine
---

### Post by woozyking on 2008-04-22
:( It works perfectly but sometimes when right click in the game, the right click menu appears (the one that would appear on the top of each window if right clicked)

Please help, thanks in advance:popcorn:

ps: my computer is that last Thinkpad T43 model with IBM logo on:lolflag:

---

### Post by grifter13 on 2008-04-22
> **woozyking said:**
> :( It works perfectly but sometimes when right click in the game, the right click menu appears (the one that would appear on the top of each window if right clicked)

Please help, thanks in advance:popcorn:

ps: my computer is that last Thinkpad T43 model with IBM logo on:lolflag:

You got Warcraft working in Wine?!  Is this regular Warcraft or World of Warcraft?  If World of Warcraft, could you send me the link to how you did it?

Grift

---

### Post by woozyking on 2008-04-22
No sorry, Grift, I am talking bout Warcraft 3

---

### Post by vexorian on 2008-04-22
> **grifter13 said:**
> You got Warcraft working in Wine?!  Is this regular Warcraft or World of Warcraft?  If World of Warcraft, could you send me the link to how you did it?

Grift
provided you got good graphics card support WoW is not a problem in Linux, It's platinum: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329)

---

### Post by soxs on 2008-04-23
plx post what version you are using, what graphicscard/driver, desktop environment, if 3d desktop, and whatever. Thx

---

### Post by Jexel on 2008-04-23
this happens when you press alt+rightclick.

You have to go into System->Preferences->Keyboard Shortcuts and change one of the settings. I think it's "Activate Windows Menu".

---

### Post by soxs on 2008-04-23
If that solution will notwork, you can still run wc3roc/tft in its own xserver (whcih aswell boosts speed)
Have a look here (best to read through the whole text)
[http://gaming.gwos.org/doku.php/wine:winestuff](http://gaming.gwos.org/doku.php/wine:winestuff)

---

### Post by grifter13 on 2008-04-23
> **vexorian said:**
> provided you got good graphics card support WoW is not a problem in Linux, It's platinum: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329)

Thanks for the pointer.  I will try this tonight, to think I can get ride of my Windows partition.... oh the joy!!!:lolflag:

Grift

---

### Post by woozyking on 2008-04-23
First of all, thank you guys.

Then after Jexel's hint, I started to check how exactly would I invoke that annoying menu to pop up in the game. I realized it's Alt + Right Click (left if it's left handed mouse). I was wondering why this happens only when I encounter enemies (I have to press alt to check their hp status, lol).

However, the key shortcut configuration will not work at all for this since Alt + Right Click is not a shortcut, it's a feature of the windows manager. So I changed the movement key from alt to contrl and that solved all of my problems!

Thank you guys again, especially Jexel and soxs (and I read that, but think I wouldn't need a seperate xserver session for playing warcraft since it's running smoothly already).

---

