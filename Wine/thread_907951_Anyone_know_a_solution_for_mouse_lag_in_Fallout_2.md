---
title: "Anyone know a solution for mouse lag in Fallout 2?"
date: 2008-09-02
forum: Wine
---

### Post by donahuejw on 2008-09-02
I was able to successfully install Fallout 2 on Ubuntu 8.0.4 using Wine v1.0.  However, for some reason I have terrible mouse lag when the cursor is over the main play window.  As soon as the cursor moves into the control panel at the bottom 3rd of the screen it moves OK again, and the intro movie runs very smoothly, but the lag in the main window makes the game unplayable.

I've tried a variety of suggestions that I came across on various forums - change the process priority, using a secondary X server, etc., but none of them work.

Has anyone seen this behavior when running Fallout 2 under Ubuntu/wine and managed to fix it?  If so, please share your secrets :confused:

btw, I'm starting from the terminal, and here is some of the output:

xxxx@home-laptop:~$ wine c:/Program\ Files/BlackIsle/Fallout2/fallout2.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x33f194,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(640,480)
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(640,480)
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(640,480)
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(640,480)
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(640,480)

---

### Post by YokoZar on 2008-09-02
What exactly is "mouse lag" ?

---

### Post by donahuejw on 2008-09-02
Sorry, I should have been more specific.

What I mean is that the on-screen cursor, whether the red hexagon used to move your character or the other cursors used to interact with the environment and NPCs, lags behind where it should be relative to the absolute movement of the mouse (or touchpad in my case).  When I move the mouse down into the bottom control panel, for combat or to access the character sheet, etc., the cursor does not lag behind the mouse at all.  It is only when the cursor is up in the main window.

I've also noticed that my character moves somewhat slowly as well, even when running, almost as though the FPS is lower than it should be.  I'm assuming this is related.

---

### Post by YokoZar on 2008-09-02
> **donahuejw said:**
> Sorry, I should have been more specific.

What I mean is that the on-screen cursor, whether the red hexagon used to move your character or the other cursors used to interact with the environment and NPCs, lags behind where it should be relative to the absolute movement of the mouse (or touchpad in my case).  When I move the mouse down into the bottom control panel, for combat or to access the character sheet, etc., the cursor does not lag behind the mouse at all.  It is only when the cursor is up in the main window.

I've also noticed that my character moves somewhat slowly as well, even when running, almost as though the FPS is lower than it should be.  I'm assuming this is related.
I managed to play Fallout 2 through a few means.  I raised the mouse sensitivity in the game's options menu.  I was also running the game in a virtual desktop, using:
```
wine explorer /desktop=fallout,640x480 fallout2.exe
```

---

### Post by donahuejw on 2008-09-02
Unfortunately, that doesn't work.  The mouse movement is still unusably jerky.

---

### Post by edutiao on 2009-10-10
I managed to get fallout2 working smoothly with the following regedit entries(you may have to create those):

```
[HKEY_CURRENT_USER\Software\Wine\AppDefaults\fallout2.exe]
"Version"="win98"

[HKEY_CURRENT_USER\Software\Wine\AppDefaults\fallout2.exe\Direct3D]
"DirectDrawRenderer"="gdi"
"RenderTargetLockMode"="readtex"

[HKEY_CURRENT_USER\Software\Wine\AppDefaults\fallout2.exe\X11 Driver]
"Decorated"="N"
"DXGrab"="Y"
"Managed"="Y"
```

The "RenderTargetLockMode"="readtex" option does something to the palletes (i think), wich would make the game sluggish (fade in/out annoyance).

On a second note, i have "OffScreenRenderingMode"="backbuffer" in "software\wine\Direct3D" (global settings). Not sure if this changes anything, but as i'm away from the laptop can't test either.

Results may vary, but i managed to get F2 running smoothly and in fullscreen mode - for the 1st time!

Cheers

---

