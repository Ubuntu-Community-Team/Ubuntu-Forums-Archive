---
title: "TES: Oblivion window problems."
date: 2014-08-08
forum: Wine
---

### Post by blahman179 on 2014-08-08
Long story short: I installed TES:O with PlayOnLinux fine, but when I run it:

A.) In fullscreen, it screws up my resolution, forcing me to reboot, (shows the top left corner of my screen at a low resolution.)

B.) In windowed mode, the window and Wine icon disappear, even though I can still hear audio from the game until I close it with PlayOnLinux.

I'm running Ubuntu 14.04.1, using WINE 1.7.22 and using PlayOnLinux version 4.2.2

Literally every other game I've installed has worked perfectly fine, even games said to have problems I've run perfectly.

Any help would be appreciated.

---

### Post by blahman179 on 2014-08-09
Through Trial and Error, I've found a fix for myself:

When in full screen, the screen re-activates once I get to the main menu.

I've found out that, when ALT-TAB-ing away from the game forced the system resolution down, but was still acting like it was at a higher resolution.

So I went into the oblivion.ini file, enabled fullscreen again, and set the resolution to the one Ubuntu is using.

Now to actually see if the game itself runs.

Edit:

The game runs, but it's a bit jerky for some reason: in Windows it runs beautifully on my system, even at near max settings.

Switching back to the Open Sorce driver has the Oblivion launcher listing it properly now, an HD 6400 series.



I still have no idea why windowed mode doesn't work.

---

