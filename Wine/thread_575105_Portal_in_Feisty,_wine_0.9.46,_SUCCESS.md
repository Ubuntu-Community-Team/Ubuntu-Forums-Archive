---
title: "Portal in Feisty, wine 0.9.46, SUCCESS"
date: 2007-10-13
forum: Wine
---

### Post by oedipuss on 2007-10-13
Yay, after some fussing with corrupted graphics, I've managed to run portal in feisty!

Simply, select the desktop shortcut's properties, and add '-dxlevel 81' (without the quotes) at the command field. No more green textures, everything looks nice. It even lets me use bloom (says hdr too, but I think that's a dx9 only feature). 

So, apart from the minor hassle of shutting down compiz, the occasional verifying game data with steam (to get rid of the busy registry error), and some fps drop relative to windows, the game runs fine =D
Haven't experimented much with it, maybe it'll run smoother with some of the advanced settings tuned down.

---

### Post by danimall on 2008-03-27
Awesome, this post made my day.  Portal runs smooth as hell.  Only thing is that I can't change the screen resolution without it crashing on me.  It's not that big of a deal though.  I was just trying to go widescreen since I was running it on a laptop.

---

### Post by volanin on 2008-04-07
Well, try to start it with '-width 1280 -height 800', or whatever your resolution might be!


But now... I need some help too!
I have wine 0.9.58 installed on gutsy, and an intel graphics board.
Whenever I try to start portal, it gets to the loading screen and freezes.

Everybody here seems to be running it with a nvidia.
Is it possible to run it on a intel?


Steps that I do to start the game:
1. Delete .wine directory to start clean.
2. winecfg: change sound to alsa.
3. Let wine download gecko.
4. Disable compiz.
5. run: wine hl2.exe -steam -game portal

Any suggestions?
:)

---

