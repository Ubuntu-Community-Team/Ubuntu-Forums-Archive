---
title: "Team Fortress 2"
date: 2008-05-26
forum: Wine
---

### Post by Tyke91 on 2008-05-26
I'm trying to install TF2 on my dad's Xubuntu computer, and I'm getting some issues with the ATI x600 graphics card. 

The game will start up fine until it gets to the front page, at which point it will become a black screen. The buttons and sounds still work however, because I can hear the sound generated when the mouse moves over the buttons, and I can actually start a game by clicking randomly (of course, this means nothing because the screen is completely black) 

I tried disabling the pixel shader support in wine, and It allowed me to see the loading screen for the front menu, but as soon as the game was finished loading, it threw an error message saying that pixel shader 1.1 or higher was required. and promptly quit the game.


i am forcing -dxlevel81 

any help?

---

### Post by Kronie on 2008-06-04
wow, im having same issue with my x600 card T_T

---

### Post by Sleaka J on 2008-06-05
Try adding the launch option of -window as well. I have a similar problem with TF2 when trying to launch in fullscreen, but I don't get any sound. If I run in a window and just switch to fullscreen once I get to the menu, it works after that (albiet slowly).

I'm running an nVidia 7600GS, so it doesn't seem to be video card related, though I understand there are a few issues with ATI drivers in Linux.

---

