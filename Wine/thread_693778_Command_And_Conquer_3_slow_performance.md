---
title: "Command And Conquer 3 slow performance"
date: 2008-02-11
forum: Wine
---

### Post by mad_max0204 on 2008-02-11
I managed to install cnc3 with no major problems.
EReg.exe was problematic since I just saw a white screen. Killed the proces and everything went on fine. Patched the game with 1.09 patch and started. Menu is fast, video plays good, load is much faster than on windows BUT game itself is soooo slow. I set the resolution 1680x1050 and everything on high (game is fluid on windows in this setup) and its just too slow to be playable. Gfx is good but there seems to be no shadows. I dled those two dlls d3dx9_29.dll and gdiplus.dll, tried with lower settings and resolution but no avail. I set the game to run in WinXP winversion.

I have a 7900GTX gfx and a fairly good rig.

---

### Post by mad_max0204 on 2008-02-11
I have some free time on my hands so I'm compiling new 0.9.55 wine with proper libs as mentioned in WineOn64bit how to. I'll then try to get everything working. I'm not doin all this because I'm desperate to play games on linux I'm doin this because I learned a lot just trying to get some everyday things to work (like audio and video players, desktop effects,...).

PS This must be a beginning of a beautifull friendship :D

---

### Post by GSF1200S on 2008-02-11
I cant remember what the options are, but in graphic options, its the top two options on the right (I think GFX and shadows) need to be turned all the way down. All the other options can be left on high and it will run smooth.

Im on an Nvidia 7600 256 MB same resolution (the graphics are at medium to low though), and it runs super smooth...

---

### Post by mad_max0204 on 2008-02-11
wow manual compile went smooth. so did install. I'm gonna try and install cnc3 now and setup like you just said.
one more thing, is that normal that shadows and lightning dont work in wine ??
I read for other game and they also have problems with dynamic lightning and shadows. I think that these two give games their flawour.

PS I learned how to link libraries. its awesome that theres always something that u can learn in linux

---

### Post by sandy8925 on 2008-12-03
U could try using native dlls.It increased performance a lot for me.However the native d3dx9.dll seems to be causing problems.

I haven't noticed if there are shadows - I was too busy playing!

Also run it from terminal using:

WINEDEBUG=-all wine CNC3.exe

or

WINEDEBUG=fixme-all wine CNC3.exe

---

### Post by Psyphre on 2009-03-29
I want to try but im curious as to how playable it is? Can you play online with other people without any issues?

---

