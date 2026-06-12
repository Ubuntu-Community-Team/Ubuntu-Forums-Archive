---
title: "Tip on Steam + Wine, setting dxlevel"
date: 2007-08-12
forum: Wine
---

### Post by ZarathustraDK on 2007-08-12
Don't know if this has been emphasized before, but here goes.

I've had loads of trouble with running Steam through wine, probably mostly because of complicated howtos  on how to tweak steam using wine throgh svn, compiling it yourself or any other highly customized wine-version.

Specifically I had a lot of trouble with the graphics. Textures were either corrupted, running very slow, crashing and everything in between (especially in Half-Life Episode One).

Part of the reason for this is (I guess) that a lot of newer steam-games utilize some exotic new directx-features which is not yet supported by wine. This problem can be bypassed by starting every steam-game with the "-dxlevel 70" property added (right-click your game in the gamebrowser ---> properties ---> set launch parameters).

This sets the directx version used in the game to directx 7.0, and rids the game of all those fancy graphic-features and makes the game playable (and much MUCH more faster). Counter-strike Source for instance runs completely fluid as in native windows on my comp, whereas with directx 9 it is a very choppy and unplayable experience. Sure it may not look as fancy as native with eye-candy, but blablabla. No need for any -opengl flags anywhere, just wine steam.exe and set the -dxlevel.

Cheers

---

### Post by pierlo on 2008-12-18
cool! any idea how to add that launch option on a non-steam version of css?

---

### Post by doorknob60 on 2008-12-18
Probably just add it the the end of the launcher/command you use. (eg: wine C:\\Program\ Files\\COunter Strike Source\\CSS.exe -dxlevel 81) <-- Obviously make surwe it's the right path,that's p[robably wrong. And -dxlevel 81 works for most people (including me in TF2) in recen versions of Wine, no need for 70 (I didn't even think that 70 would work)

---

