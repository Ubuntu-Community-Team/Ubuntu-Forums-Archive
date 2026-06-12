---
title: "another ATI direct rendering thread"
date: 2008-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by LoneWolfJack on 2008-03-10
Ok, I guess this could go to the multimedia forums as well but as I'm running x64...

A couple days back I have been fiddling with the ATI drivers for HOURS to get that pittyful excuse of a driver working... now I'm unsure as to whether I actually succeeded.

"glxinfo | grep rendering" says
> 
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect


but "DISPLAY=:0 glxinfo | grep rendering" says:
> direct rendering: Yes

"fglrxinfo" says:
> 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1800 Series
OpenGL version string: 2.1.7281 Release


3d acceleration works if I add the display thing ("display:=0 wine program.exe")... so is this how this driver is supposed to work, or is there a config problem?

Do I need the display thing because of my two monitors? And if so, can't the driver be configured so it always assumes display:=0 automatically?

thanks for any help.

---

### Post by Melcar on 2008-03-10
I thought the driver did not support 3D accel. on the second monitor in a dual screen setup?  Or is that just video playback?

---

### Post by LoneWolfJack on 2008-03-10
that was not what I meant.

If I use 
```
wine program.exe
```

I'm getting garbage on any program that needs 3d acceleration.

If I use
```
DISPLAY=:0 wine program.exe
```

The same program works perfectly.

This problem is NOT limited to wine in any way though.

Also, I installed Criticalmass (a classic space invaders like game from the repos) which worked fine until I "fixed" the drivers... now it's so slow it's not usable any more.

So... any ideas on how the driver fixed 3d acceleration for some things but broke it for others?

---

