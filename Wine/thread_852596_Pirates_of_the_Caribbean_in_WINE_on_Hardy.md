---
title: "Pirates of the Caribbean in WINE on Hardy?"
date: 2008-07-07
forum: Wine
---

### Post by hunt.topher on 2008-07-07
I was ecstatic when I got Heroes of Might and Magic III working (and working perfectly) with Wine on Ubuntu. I read in the Wine AppDB that [Pirates of the Caribbean]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=5356&iTestingId=25671") works great on some recent releases of Wine in Ubuntu and Debian Etch. However, Pirates isn't working so well for me. I'm pretty sure it's something to do with the 3D engine initialization.

Program installs perfectly and when I run PotC, either from terminal or from the .desktop link, the loading proceeds without problem. The main menu screen looks and works perfectly as well as the theme music. But I click "New Game" and it shows the loading screen; then it freezes on the loading screen, and if I forced Wine to run in a windowed session, it crashes and restarts X; if I let PotC run fullscreen, it freezes and I'm forced to do a hard restart.

I've tried this on Wine 0.9.59, on Wine 1.0 rc2, and on Wine 1.1.0. On .9.59 and 1.1.0, the game works as described above. In 1.0rc2, it crashes while loading and kicks me back to the desktop. I have tried running PotC with Wine configured for Win98, Win2K, WinME, and WinXP with no observable difference in results.

This is on an Inspiron 1520 with Ubuntu 8.04. My graphics card is Intel GL960(?) and I have a 1.5 GHz processor (more than enough for this game). I haven't done any special configuration of Wine and the only other programs installed are Riven, Acrobat Reader 5, and Windows Media Player 9. Once as PotC crashed while loading the new game, I captured the output in terminal and it is attached below.

I'd love any suggestions on how I could get Pirates working on Hardy... nostalgia...

---

### Post by lisati on 2008-07-07
One of my memories of visiting Disneland at the age of 10 (more years ago than I sometimes care to remember) was that the Pirates of the Caribbean ride was awesome.

(BTW I haven't actually played the game.)

---

### Post by hunt.topher on 2008-07-10
OK so I dug deeper through my own logfile after posting here and came up with some more specifics: it turns out the freezeup was caused because the game graphics use Direct3D's Vertex Shader function, but somehow WINE seems to be conflicting with my graphics driver (Intel GM965/GL960, known not fully supported) and as a result the game freezes on loading 3D graphics. If I disable Pixel Shader, the game **does** load, except all textures minus the main character are lost - NPCs, scenery, objects etc. are all white and textureless.

O Sage Ubuntu Community... Is there any hope? Any suggestions? Or should I just wait until my graphics card is better supported?

 - Topher

---

