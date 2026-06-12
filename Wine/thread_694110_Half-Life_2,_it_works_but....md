---
title: "Half-Life 2, it works but..."
date: 2008-02-11
forum: Wine
---

### Post by MichaelLerch on 2008-02-11
I can't see anyone.  I can start a game, join a game, etc but I can't see players, I don't even see my weapon models.  However, I can see if a player has grenades or not.

What can I do to fix this?

I have Wine v0.9.54; Ubuntu 7.10

System Specs:
Quad Core 2.4GHz Intel
3GB DDR2 RAM
ATI Radeon HD2600XT 512MB

It's a Dell XPS 420 (factory install of Windows Vista 32bit Home Premium). I self-installed Ubuntu.  Everything else works fine, just I can't see the models.

Any ideas?

---

### Post by iAlta on 2008-02-11
I have the same problem. I have a ATI Radeon 2400. I assume the graphics card is the problem... as no one on winehq seems to have this problem..

---

### Post by MichaelLerch on 2008-02-11
I'm going to update to the latest version of Wine and see if that works.  I got the game to work by updating to 0.9.54, so maybe 0.9.55 will fix it... since it does have improvements on Direct3D :)

---

### Post by MichaelLerch on 2008-02-11
Alright, and the results are.... performance is superb, and I can see small bits of the models, like I saw a players neck.  So it's gotta be something..

---

### Post by iAlta on 2008-02-12
Yeah... You can see the neck and the eyes..
I also just updated fglrx, but that didn't work either.. :/

---

### Post by MichaelLerch on 2008-02-12
I figured it out!  

Add this to the command line when you start the game from Steam

-novid -dxlevel 70

-----------------

the only problem is that I can't figure how to save my video settings.  It sets Model Detail to MED, and everything else to LOW.  and it sets the resolution to 800 x 600 (or 640 x 480) which ever.  Can't remember.  but I can see everything, it's working really nicely. :)

You can adjust the settings in-game to fit your needs, I set everything to MAX and joined a multiplayer game and, worked.  I played for 2 hours today. :) 

Just the DXLevel -has- to be 70 (DirectX 7).  It's either WINE or ATI drivers that's causing the problem.

---

### Post by MichaelLerch on 2008-02-12
OMG I FIXED IT!

I have a Vista installation and what I did was copy **ALL** the DirectX / D3D files from Windows/System32 to my Wine/Windows/System32/  

I removed the -dxlevel 70

Tested.  IT WORKED!

If you need the DX files, I'll zip/rar them up and post a link to it here. :)  Just ask for it

---

### Post by The Noble on 2008-02-13
That's not the most suitable solution, sadly. I'm glad it worked, but something is amiss here. It is generally assumed that the ATI drivers are the problem, as .9.54 works fine on my Nvidia 8400 GS with DX 8.1. One thing interests me though: Are you using Direct X 9? It runs like a dog on my system due to poor support for version 9, so if this is making it work in DX9 mode, this could be interesting.

I don't reccommend this fix for anyone, but if you are desperate for Half life 2 and don't mind screwing up wine, this could help pinpoint where the problem lies. Hell, it may even gen better performance.

---

### Post by iAlta on 2008-02-13
> **MichaelLerch said:**
> OMG I FIXED IT!

I have a Vista installation and what I did was copy **ALL** the DirectX / D3D files from Windows/System32 to my Wine/Windows/System32/  

I removed the -dxlevel 70

Tested.  IT WORKED!

If you need the DX files, I'll zip/rar them up and post a link to it here. :)  Just ask for it
Hey, sure. I wouldn't mind those files, if you don't mind.

---

### Post by Sockerdrickan on 2008-02-13
It's probably an ati graphics driver bug

---

### Post by The Noble on 2008-02-14
> **Tux0r said:**
> It's probably an ati graphics driver bug

What is weird is that he fixed it using some windows dll's. This should not work if it was purely an ATI problem. I'm going to guess that it is a mix of how DX9 is implemented in wine and the drivers, not just one or the other. Either way, if someone can see if this actually works it would benefit the wine devs to know what is going on.

---

### Post by iAlta on 2008-02-14
wine-debug?

anyways, the dxlevel70 workaround works for me, but it crashes every time it loads a new level.. :(

---

