---
title: "Baldur's Gate II in Wine"
date: 2008-11-17
forum: Wine
---

### Post by ncanna1 on 2008-11-17
I've got Baldur's Gate II installed and working, there is just one problem that I can tell.  Whenever I try to use the multiplayer mode, the sound for my entire system cuts out.  The only way for me to restore sound easily is to reboot the entire computer.  I am turning off pulseaudio before starting the game every time to avoid choppy sound.  Again, the sound is working fine on the single player mode.  I have also tried switching the audio drivers that wine has enabled to no avail.

I'm using ubuntu 8.10 and wine 1.1.8.

---

### Post by Modax42 on 2008-11-18
some things to try:

-run BG2 in windowed mode instead of full screen
-turn off compiz
-close all other applications before launching the game
-open BG config and change all settings to '450 MHz PC' (weird, I know)
-turn off 3D acceleration
-reinstall the game, using 'compact' or 'recommended' instead of 'full'

hope this helps :)

---

