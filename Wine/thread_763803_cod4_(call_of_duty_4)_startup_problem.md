---
title: "cod4 (call of duty 4) startup problem"
date: 2008-04-23
forum: Wine
---

### Post by thefishki345 on 2008-04-23
Hi, I finally managed to compile wine with 3dmark patch to run call of duty 4, wine is installed properly, I get all the right output when I type wine in console, winecfg works. I used this tutorial:[http://www.filledvoid.com/2008/02/16/compiling-wine-for-ubuntu-gutsy-gibbon-64-bit](http://www.filledvoid.com/2008/02/16/compiling-wine-for-ubuntu-gutsy-gibbon-64-bit) 

and am using hardy heron 8.04 beta.

So the problem is:
when I click the icon to run cod4 (singleplayer or multiplayer) in the panels it says ¨starting call of duty 4¨ then...nothing. When I try and run it again, it says ¨it appears cod4 did not close last time, would you like to run in safe mode?¨ so even if I click Yes _or_ No it still crashes. 
I am using wine 0.9.60 and, sadly I am running 64 bit linux-its like being left handed-which, ironically, I am  )


EDIT: also. when I run: ```
[B]$ cd ~/.wine/drive_c/Program\ Files/Activision/Call\ of\ Duty\ 4\ -\ Modern\ Warfare/
~/.wine/drive_c/Program Files/Activision/Call of Duty 4 - Modern Warfare$ wine iw3sp.exe[/B]
```


I get:
[terminaloutput]
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:wgl:X11DRV_ChoosePixelFormat No OpenGL support compiled in.
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl
wine: Unhandled page fault on read access to 0x00000000 at address 0x7eba4024 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7eba4024).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7eba4024 ESP:0032f88c EBP:0032f8e4 EFLAGS:00010212(   - 00      - RIA1)
 EAX:0032f8b0 EBX:7ebb7678 ECX:7ebb7e80 EDX:00000000
 ESI:00138520 EDI:7ebb7e7c
Stack dump:
0x0032f88c:  7ebb7e7c 00000000 000008ec 7eb66854
0x0032f89c:  0000000a 0000000a 0000000a 0000000a
0x0032f8ac:  00000000 0032f8fc 0032fafc 0032fcfc
0x0032f8bc:  0032fd1c 0032fd24 0032fd28 0032fd2c
0x0032f8cc:  0032fd30 0032fd34 0032fd44 00000000
0x0032f8dc:  00138520 7b88b210 0032fd60 00593836
Backtrace:
=>1 0x7eba4024 IDirect3D9Impl_GetAdapterIdentifier+0x84(iface=0x138520, Adapter=0x0, Flags=0x0, pIdentifier=0x32f8fc) [/home/josh/wine/dlls/d3d9/directx.c:124] in d3d9 (0x0032f8e4)
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature 665f4c49 in module L"iw3sp"
  2 0x00593836 in iw3sp (+0x193836) (0x0032fd60)
  3 0x00595626 in iw3sp (+0x195626) (0x0032ff08)
  4 0x7b876447 start_process+0xc7(arg=0x0) [/home/josh/wine/dlls/kernel32/process.c:839] in kernel32 (0x0032ffe8)
  5 0xf7e48a37 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7eba4024 IDirect3D9Impl_GetAdapterIdentifier+0x84 [/home/josh/wine/dlls/d3d9/directx.c:124] in d3d9: movl	0x0(%edx),%ecx
124	    hr = IWineD3D_GetAdapterIdentifier(This->WineD3D, Adapter, Flags, &adapter_id);
Modules:
Module	Address			Debug info	Name (74 modules)
PE	  400000- 2101000	Export          iw3sp
PE	 2110000- 247f000	Deferred        d3dx9_34
PE	18000000-18033000	Deferred        binkw32
PE	21100000-21197000	Deferred        mss32
ELF	7b800000-7b92c000	Dwarf           kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e2ba000-7e2ec000	Deferred        uxtheme<elf>
  \-PE	7e2c0000-7e2ec000	\               uxtheme
ELF	7e2ec000-7e312000	Deferred        msacm32<elf>
  \-PE	7e2f0000-7e312000	\               msacm32
ELF	7e312000-7e329000	Deferred        msacm32<elf>
  \-PE	7e320000-7e329000	\               msacm32
ELF	7e329000-7e3ec000	Deferred        libasound.so.2
ELF	7e3ec000-7e422000	Deferred        winealsa<elf>
  \-PE	7e400000-7e422000	\               winealsa
ELF	7e422000-7e427000	Deferred        libxfixes.so.3
ELF	7e427000-7e42f000	Deferred        libxrender.so.1
ELF	7e42f000-7e438000	Deferred        libxcursor.so.1
ELF	7e438000-7e456000	Deferred        imm32<elf>
  \-PE	7e440000-7e456000	\               imm32
ELF	7e456000-7e45b000	Deferred        libxdmcp.so.6
ELF	7e45b000-7e473000	Deferred        libxcb.so.1
ELF	7e473000-7e475000	Deferred        libxcb-xlib.so.0
ELF	7e475000-7e478000	Deferred        libxau.so.6
ELF	7e478000-7e55f000	Deferred        libx11.so.6
ELF	7e55f000-7e56d000	Deferred        libxext.so.6
ELF	7e56d000-7e5e8000	Deferred        winex11<elf>
  \-PE	7e580000-7e5e8000	\               winex11
ELF	7e5e8000-7e5fd000	Deferred        libz.so.1
ELF	7e5fd000-7e66d000	Deferred        libfreetype.so.6
ELF	7e66d000-7e680000	Deferred        libresolv.so.2
ELF	7e680000-7e69e000	Deferred        iphlpapi<elf>
  \-PE	7e690000-7e69e000	\               iphlpapi
ELF	7e69e000-7e6ff000	Deferred        rpcrt4<elf>
  \-PE	7e6b0000-7e6ff000	\               rpcrt4
ELF	7e6ff000-7e7a3000	Deferred        ole32<elf>
  \-PE	7e710000-7e7a3000	\               ole32
ELF	7e7a3000-7e7f9000	Deferred        ddraw<elf>
  \-PE	7e7b0000-7e7f9000	\               ddraw
ELF	7e7f9000-7e8b8000	Deferred        comctl32<elf>
  \-PE	7e800000-7e8b8000	\               comctl32
ELF	7e8b8000-7e911000	Deferred        shlwapi<elf>
  \-PE	7e8d0000-7e911000	\               shlwapi
ELF	7e911000-7ea1d000	Deferred        shell32<elf>
  \-PE	7e920000-7ea1d000	\               shell32
ELF	7ea1d000-7ea86000	Deferred        msvcrt<elf>
  \-PE	7ea30000-7ea86000	\               msvcrt
ELF	7ea86000-7eb88000	Deferred        wined3d<elf>
  \-PE	7eaa0000-7eb88000	\               wined3d
ELF	7eb88000-7ebb8000	Dwarf           d3d9<elf>
  \-PE	7eb90000-7ebb8000	\               d3d9
ELF	7ebb8000-7ec0a000	Deferred        advapi32<elf>
  \-PE	7ebc0000-7ec0a000	\               advapi32
ELF	7ec0a000-7eca4000	Deferred        gdi32<elf>
  \-PE	7ec20000-7eca4000	\               gdi32
ELF	7eca4000-7edea000	Deferred        user32<elf>
  \-PE	7ecc0000-7edea000	\               user32
ELF	7edea000-7ee78000	Deferred        winmm<elf>
  \-PE	7ee00000-7ee78000	\               winmm
ELF	7ef98000-7efa3000	Deferred        libnss_files.so.2
ELF	7efa3000-7efad000	Deferred        libnss_nis.so.2
ELF	7efad000-7efc5000	Deferred        libnsl.so.1
ELF	7efc5000-7efea000	Deferred        libm.so.6
ELF	7efec000-7f000000	Deferred        midimap<elf>
  \-PE	7eff0000-7f000000	\               midimap
ELF	f7cb5000-f7cbe000	Deferred        libnss_compat.so.2
ELF	f7cbf000-f7cc3000	Deferred        libdl.so.2
ELF	f7cc3000-f7e12000	Deferred        libc.so.6
ELF	f7e13000-f7e2b000	Deferred        libpthread.so.0
ELF	f7e41000-f7f77000	Dwarf           libwine.so.1
ELF	f7f79000-f7f98000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Activision\Call of Duty 4 - Modern Warfare\iw3sp.exe
	00000009    0 <==
0000000c 
	00000014    0
	00000013    0
	0000000e    0
	0000000d    0
0000000f 
	00000012    0
	00000011    0
	00000010    0
00000015 
	00000016    0
Backtrace:
=>1 0x7eba4024 IDirect3D9Impl_GetAdapterIdentifier+0x84(iface=0x138520, Adapter=0x0, Flags=0x0, pIdentifier=0x32f8fc) [/home/josh/wine/dlls/d3d9/directx.c:124] in d3d9 (0x0032f8e4)
  2 0x00593836 in iw3sp (+0x193836) (0x0032fd60)
  3 0x00595626 in iw3sp (+0x195626) (0x0032ff08)
  4 0x7b876447 start_process+0xc7(arg=0x0) [/home/josh/wine/dlls/kernel32/process.c:839] in kernel32 (0x0032ffe8)
  5 0xf7e48a37 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:opengl:X11DRV_wglGetProcAddress No OpenGL support compiled in.
err:wgl:X11DRV_ChoosePixelFormat No OpenGL support compiled in.
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl
wine: Unhandled page fault on read access to 0x00000000 at address 0x7eba4024 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7eba4024).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7eba4024 ESP:0032f88c EBP:0032f8e4 EFLAGS:00010212(   - 00      - RIA1)
 EAX:0032f8b0 EBX:7ebb7678 ECX:7ebb7e80 EDX:00000000
 ESI:00138520 EDI:7ebb7e7c
Stack dump:
0x0032f88c:  7ebb7e7c 00000000 000008ec 7eb66854
0x0032f89c:  0000000a 0000000a 0000000a 0000000a
0x0032f8ac:  00000000 0032f8fc 0032fafc 0032fcfc
0x0032f8bc:  0032fd1c 0032fd24 0032fd28 0032fd2c
0x0032f8cc:  0032fd30 0032fd34 0032fd44 00000000
0x0032f8dc:  00138520 7b88b210 0032fd60 00593836
Backtrace:
=>1 0x7eba4024 IDirect3D9Impl_GetAdapterIdentifier+0x84(iface=0x138520, Adapter=0x0, Flags=0x0, pIdentifier=0x32f8fc) [/home/josh/wine/dlls/d3d9/directx.c:124] in d3d9 (0x0032f8e4)
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature 665f4c49 in module L"iw3sp"
  2 0x00593836 in iw3sp (+0x193836) (0x0032fd60)
  3 0x00595626 in iw3sp (+0x195626) (0x0032ff08)
  4 0x7b876447 start_process+0xc7(arg=0x0) [/home/josh/wine/dlls/kernel32/process.c:839] in kernel32 (0x0032ffe8)
  5 0xf7e48a37 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7eba4024 IDirect3D9Impl_GetAdapterIdentifier+0x84 [/home/josh/wine/dlls/d3d9/directx.c:124] in d3d9: movl	0x0(%edx),%ecx
124	    hr = IWineD3D_GetAdapterIdentifier(This->WineD3D, Adapter, Flags, &adapter_id);
Modules:
Module	Address			Debug info	Name (74 modules)
PE	  400000- 2101000	Export          iw3sp
PE	 2110000- 247f000	Deferred        d3dx9_34
PE	18000000-18033000	Deferred        binkw32
PE	21100000-21197000	Deferred        mss32
ELF	7b800000-7b92c000	Dwarf           kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e2ba000-7e2ec000	Deferred        uxtheme<elf>
  \-PE	7e2c0000-7e2ec000	\               uxtheme
ELF	7e2ec000-7e312000	Deferred        msacm32<elf>
  \-PE	7e2f0000-7e312000	\               msacm32
ELF	7e312000-7e329000	Deferred        msacm32<elf>
  \-PE	7e320000-7e329000	\               msacm32
ELF	7e329000-7e3ec000	Deferred        libasound.so.2
ELF	7e3ec000-7e422000	Deferred        winealsa<elf>
  \-PE	7e400000-7e422000	\               winealsa
ELF	7e422000-7e427000	Deferred        libxfixes.so.3
ELF	7e427000-7e42f000	Deferred        libxrender.so.1
ELF	7e42f000-7e438000	Deferred        libxcursor.so.1
ELF	7e438000-7e456000	Deferred        imm32<elf>
  \-PE	7e440000-7e456000	\               imm32
ELF	7e456000-7e45b000	Deferred        libxdmcp.so.6
ELF	7e45b000-7e473000	Deferred        libxcb.so.1
ELF	7e473000-7e475000	Deferred        libxcb-xlib.so.0
ELF	7e475000-7e478000	Deferred        libxau.so.6
ELF	7e478000-7e55f000	Deferred        libx11.so.6
ELF	7e55f000-7e56d000	Deferred        libxext.so.6
ELF	7e56d000-7e5e8000	Deferred        winex11<elf>
  \-PE	7e580000-7e5e8000	\               winex11
ELF	7e5e8000-7e5fd000	Deferred        libz.so.1
ELF	7e5fd000-7e66d000	Deferred        libfreetype.so.6
ELF	7e66d000-7e680000	Deferred        libresolv.so.2
ELF	7e680000-7e69e000	Deferred        iphlpapi<elf>
  \-PE	7e690000-7e69e000	\               iphlpapi
ELF	7e69e000-7e6ff000	Deferred        rpcrt4<elf>
  \-PE	7e6b0000-7e6ff000	\               rpcrt4
ELF	7e6ff000-7e7a3000	Deferred        ole32<elf>
  \-PE	7e710000-7e7a3000	\               ole32
ELF	7e7a3000-7e7f9000	Deferred        ddraw<elf>
  \-PE	7e7b0000-7e7f9000	\               ddraw
ELF	7e7f9000-7e8b8000	Deferred        comctl32<elf>
  \-PE	7e800000-7e8b8000	\               comctl32
ELF	7e8b8000-7e911000	Deferred        shlwapi<elf>
  \-PE	7e8d0000-7e911000	\               shlwapi
ELF	7e911000-7ea1d000	Deferred        shell32<elf>
  \-PE	7e920000-7ea1d000	\               shell32
ELF	7ea1d000-7ea86000	Deferred        msvcrt<elf>
  \-PE	7ea30000-7ea86000	\               msvcrt
ELF	7ea86000-7eb88000	Deferred        wined3d<elf>
  \-PE	7eaa0000-7eb88000	\               wined3d
ELF	7eb88000-7ebb8000	Dwarf           d3d9<elf>
  \-PE	7eb90000-7ebb8000	\               d3d9
ELF	7ebb8000-7ec0a000	Deferred        advapi32<elf>
  \-PE	7ebc0000-7ec0a000	\               advapi32
ELF	7ec0a000-7eca4000	Deferred        gdi32<elf>
  \-PE	7ec20000-7eca4000	\               gdi32
ELF	7eca4000-7edea000	Deferred        user32<elf>
  \-PE	7ecc0000-7edea000	\               user32
ELF	7edea000-7ee78000	Deferred        winmm<elf>
  \-PE	7ee00000-7ee78000	\               winmm
ELF	7ef98000-7efa3000	Deferred        libnss_files.so.2
ELF	7efa3000-7efad000	Deferred        libnss_nis.so.2
ELF	7efad000-7efc5000	Deferred        libnsl.so.1
ELF	7efc5000-7efea000	Deferred        libm.so.6
ELF	7efec000-7f000000	Deferred        midimap<elf>
  \-PE	7eff0000-7f000000	\               midimap
ELF	f7cb5000-f7cbe000	Deferred        libnss_compat.so.2
ELF	f7cbf000-f7cc3000	Deferred        libdl.so.2
ELF	f7cc3000-f7e12000	Deferred        libc.so.6
ELF	f7e13000-f7e2b000	Deferred        libpthread.so.0
ELF	f7e41000-f7f77000	Dwarf           libwine.so.1
ELF	f7f79000-f7f98000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Activision\Call of Duty 4 - Modern Warfare\iw3sp.exe
	00000009    0 <==
0000000c 
	00000014    0
	00000013    0
	0000000e    0
	0000000d    0
0000000f 
	00000012    0
	00000011    0
	00000010    0
00000015 
	00000016    0
Backtrace:
=>1 0x7eba4024 IDirect3D9Impl_GetAdapterIdentifier+0x84(iface=0x138520, Adapter=0x0, Flags=0x0, pIdentifier=0x32f8fc) [/home/josh/wine/dlls/d3d9/directx.c:124] in d3d9 (0x0032f8e4)
  2 0x00593836 in iw3sp (+0x193836) (0x0032fd60)
  3 0x00595626 in iw3sp (+0x195626) (0x0032ff08)
  4 0x7b876447 start_process+0xc7(arg=0x0) [/home/josh/wine/dlls/kernel32/process.c:839] in kernel32 (0x0032ffe8)
  5 0xf7e48a37 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
~/.wine/drive_c/Program Files/Activision/Call of Duty 4 - Modern Warfare$
[/terminaloutput]

Please, any help would be appreciated, I really want to play this game!!!
thanks and sorry for the long command line error.

---

### Post by thefishki345 on 2008-04-25
erm...anyone??? 

also, I think the problem is that wine did not compile properly with opengl, cos when I run something like ./configure it says soemthing like ¨there is not a detected opengl thingy on this system opengl and direct3d will not be supported¨

---

### Post by snip3r8 on 2010-03-26
Last time i tried to play COD4 on wine it made my entire OS crash.

---

### Post by snip3r8 on 2010-03-26
in fact ,wine has never quite worked for me,so i just dual boot with vista

---

