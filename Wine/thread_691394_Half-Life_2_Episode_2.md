---
title: "Half-Life 2: Episode 2"
date: 2008-02-08
forum: Wine
---

### Post by kougaru on 2008-02-08
I've successfully played HL2 and EP1, but EP2 seems to cause problems. At first it gave me an error about Directx 8. To fix that error I had to enable pixel shaders in winecfg. Since I have an ATI card thats not a very good idea. It starts now, but the menu screen gives me a garbled mess.

I'm sure it's because the Pixel Shaders are enabled, but without them enabled I get the Directx 8 error.

Does anyone have any ideas?

---

### Post by jakommo on 2008-02-08
Did you check [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9421](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9421) ?
btw which version of wine are you running?

---

### Post by kougaru on 2008-02-08
I checked the AppDB but I couldn't find anything relating to the issue I'm having.

I'm using Wine 0.9.54

---

### Post by kougaru on 2008-02-09
Well I got a little farther, I enabled Vertex Shaders and I now it loads somewhat. But a lot of things are black and the all the text is missing. I can start the game and everything loads but it grinds to a halt a few seconds in.

Anyone have any ideas?

---

### Post by kougaru on 2008-02-09
Well, I managed to navigate my way through the menus to the graphics settings and managed to play the first few minutes of the game, but the lighting is still screwed up and lots of things are black. It makes it difficult to know where I'm going in some places because of it. The text is still gone. It shows up briefly but disappears again.

---

### Post by jakommo on 2008-02-09
wine 0.9.55 was released some days ago, maybe you should try this.

---

### Post by dormedas on 2008-02-09
If you want to game on Linux "reliably," I'd buy the Nvidia equivalent of your graphics card instead of running the ATI. drivers for Nvidia are much better. I got HL2:EP 2 working by adding the parameters " -novid -dxlevel 80 -preload " Worked fine, all textures, models, sounds perfect. Ran slow because my computer is crap, but it was all perfect.
(NVIDIA GeForce FX 5500 w/ intel celeron 1.8 GHz and 512 MB RAM .. ugh)

---

### Post by coltrane on 2008-03-15
> **dormedas said:**
> If you want to game on Linux "reliably," I'd buy the Nvidia equivalent of your graphics card instead of running the ATI. drivers for Nvidia are much better. I got HL2:EP 2 working by adding the parameters " -novid -dxlevel 80 -preload " Worked fine, all textures, models, sounds perfect. Ran slow because my computer is crap, but it was all perfect.
(NVIDIA GeForce FX 5500 w/ intel celeron 1.8 GHz and 512 MB RAM .. ugh)

I also got HL2:EP 2 working, everything works just as if it was windows, but when creatures like antlions or headcrabs are around the game slows right down.
My PC is a XP4000 dual core with nvidia 6600GT Graphics card and 2 Gig of RAM.
If anyone got this game working at full speed, I'd like to know what their spec's are  
and what else they did, the renice command only got me so far.

---

