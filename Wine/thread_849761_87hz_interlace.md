---
title: "87hz interlace"
date: 2008-07-04
forum: Wine
---

### Post by arvinkebob on 2008-07-04
I just installed WINE on Ubuntu 8.04 about 1 week ago. I've installed four games, GTA: Vice City and San Andreas, Halo, and Just Cause all of which worked perfectly fine until now. 

Each game started off with my desktops resolution and refresh rate (1024x768@85Hz) but have now decided to start in 87Hz interlaced. I don't know what exactly I could've done to cause this.

There were a few suggestions on the net on how to fix this such as to force the HorizSync and VertRefresh to only display in 85Hz (HS-30.0-80.0, VR-85.0-85.0) but that didn't work. I tried disabling DynamicTwinView in xorg.conf and it helped somewhat, but the refresh rate only went to 60Hz which I hate. The only two games that still works fine is Halo since it has an option to manually change refresh rate. Just Cause also works fine regardless of it not having an option to change the refresh rate. The two GTA games are the only ones that don't work.

Overall, the actual Linux resolution is fine, and native games such as Doom 3 run at 85Hz without a problem so it's narrowed down to WINE. Do I have to remove my .wine folder and re-install or is there a fix for this. My WINE version is 1.1.0.

Thanks for any help.

---

### Post by cogadh on 2008-07-06
The GTA games run at a 60Hz refresh rate by default. There is no option to change that in the game at all. It is not a problem with Wine at all, its just the way the games work.

---

### Post by arvinkebob on 2008-07-07
I see. I've messed around and so much and found one way to have the game run at my native 85Hz. Every time I log in, I run nvidia-settings, change my resolution to 1280x1024 and run GTA, quit the game and change my res back to 1024x768@85Hz and run the game again. It's a pretty quick fix and the game runs at 85Hz. I just found it a while ago and it's not too hard to do it either.

Just one more question off topic. Can you run d3d9 hacks or game "trainer's" with games running in WINE? Or will they not work?

---

