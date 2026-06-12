---
title: "WoW in Wine runs fine but the Keyboard does not work"
date: 2007-05-12
forum: Wine
---

### Post by adromidon on 2007-05-12
Ok I am running Wine and WoW when i load the program WoW runs smooth and fast however i can not use the keyboard to enter my username and password it is like Wine is not emulating my keyboard.

Is there a way to check and see if Wine has my keyboard emulated properly

---

### Post by hikaricore on 2007-05-13
This has nothing to do with "keyboard emulation".

I've had this problem under Kubuntu and also Ubuntu if certain conditions are present.

The first thing you're going to want to do is run:

```

winecfg

```

Click on the graphics tab, then UNcheck: Allow the window manager to control the windows.

Click ok then try starting WoW again.

This solved the issue for me in some cases, other times I found that (most often the KDE) desktop refused to release control of my keyboard, and my only choice was to launch the game with Tip 2 of the [Ubuntu WoW HowTo]("http://help.ubuntu.com/community/WorldofWarcraft").  Test this out befre positing back here that my fix did not work.  This method will launch WoW in it's on X session and avoid the possibility of another application "holding" keyboard control.

Good Luck,

--Aaron

---

### Post by xtek0 on 2008-02-29
It doesnt work for me is there any file?

---

### Post by mr_noob on 2011-08-02
After 4years your trick still works. At least for me it did

---

