---
title: "Arcanum"
date: 2007-08-01
forum: Wine
---

### Post by Xenophoribic on 2007-08-01
I'm trying to run Arcanum. It installed without any problems, but now when I try to run it, the screen goes black like it's loading, and immediately goes to desktop. Terminal output is this:

```
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x199080) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x198da8)->(0x10024,00000011)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x198da8)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock

```

I'm running Wine version 0.9.42.

---

### Post by Xenophoribic on 2007-08-01
Bump

---

### Post by hikaricore on 2007-08-01
Are you running it in opengl mode?

There's some info here if you havn't seen it.
[http://appdb.winehq.org/appview.php?iVersionId=3476](http://appdb.winehq.org/appview.php?iVersionId=3476)

Please add your info to the AppDB as it seems the game was previously uninstallable via WINE.  ^_^

> 

Wine compatibility
What works:
- all works fine with some issues.

What was not tested:
- network game

Tested versions
App. version	Wine version	Installs?	Runs?	Rating
1.074	20050725	no	yes	Silver

For best results use flags:

-doublebuffer -no3d

(example: wine Arcanum.exe -doublebuffer -no3d)

and same x server and game color depth.

Selected test results (selected in 'Test Results' table below)

What works
Game play and copy protection works, but it was prone to crashing due to resource leaks after an hour or so of playing. Changing DirectDrawRenderer to "opengl" removed the crashes almost completely but caused the in-game cursor to leave a trail of (minor) graphical corruption.


What does not
Installation did not work. Still have to use Cedega to install.


What was not tested

Multiplayer was not tested.


Additional Comments

---

### Post by Xenophoribic on 2007-08-01
Thanks for the reply. That actually eliminated some of the error messages, but I'm still getting the same blank screen followed by kick to desktop.

I'm not running it in OpenGL, I'm just using the regular "wine ..." and now with the added flags.

I saw that one post on there said that changing it to run in 16bit color got it going, but no explanation on how to do that. Can anyone tell me?

---

### Post by Xenophoribic on 2007-08-02
Bump

---

### Post by Xenophoribic on 2007-08-03
Bump

---

### Post by Xenophoribic on 2007-08-03
Bump

---

### Post by hikaricore on 2007-08-03
Please only bump your own thread **once ever 24 hours**.

Thanks.

--Aaron

---

### Post by Xenophoribic on 2007-08-04
Bump, I really want to play this game <_<

---

### Post by macksting on 2008-01-05
Figgers. Same problem I have, and the query has just begun at the same time.
Maybe it's something about winter months that makes us want to play Arcanum. Or maybe it's not being able to run GearHead in Debian.

---

### Post by SoliDphantoM on 2008-02-12
Just recently installed this and first game I've gotten to work for the most part smoothly in wine!

Are you running the game with the flags -no3d and -doublebuffer?

```
wine Arcanum.exe -no3d -doublebuffer
```

---

### Post by SpaceCowboyMA on 2008-07-07
Having similar issues getting Arcanum going:

[FONT="System"]```

chris@host:~/.wine/drive_c/Sierra/Arcanum$ wine Arcanum.exe -doublebuffer -no3d 
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32f744,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(800,600)
chris@host:~/.wine/drive_c/Sierra/Arcanum$

chris@host:~/.wine/drive_c/Sierra/Arcanum$ uname -a
Linux host 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux
chris@host:~/.wine/drive_c/Sierra/Arcanum$ wine --version
wine-1.1.0
chris@host:~/.wine/drive_c/Sierra/Arcanum$
```[/FONT]

Have 1.074 and no-cd exe.  Any library overrides needed?  Any ideas?

---

### Post by SpaceCowboyMA on 2008-07-10
Update-- Got this working now with [Unofficial Arcanum Patch v080708 *FINAL*]("http://www.rpgcodex.net/phpBB/viewtopic.php?t=23720&start=1450&postdays=0&postorder=asc&highlight=") over v1.074.  Had to install in Windows and then copy Windows install into wine dir.  Running fine with -doublebuffer -no3d.

---

### Post by Grps on 2009-04-27
I've managed to install but it doesn't run.

I've tried with both -no3d -nodoublebuffer
and with -no3d -doublebuffer
and everytime the screens just goes black then back to desktop.

Heard that changing the screen color to 16 bit help.
How do you do that? Change the color i mean.

---

### Post by Raziekiel on 2009-05-20
bump
Also trying to get this game running, but I can't get any farther than Grps did. Any ideas??

---

### Post by Raziekiel on 2009-05-21
I managed to get the game to work somewhat by installing it in windows, and then copying the entire /Sierra/Arcanum folder to my wine Drice_C. However, when I use -no3d the game clicks twice for everyone mouse click, and when I don't use -no3d I get graphical artifacts too bad ot play.

---

