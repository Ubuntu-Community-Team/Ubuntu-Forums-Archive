---
title: "ati drivers no longer loading"
date: 2005-03-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by kubla on 2005-03-12
Has anyone else had Xorg suddenly refuse to load the fglrx driver and fall back to mesa?

fglrxinfo now reports:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

Poking around the Xorg log files, I'm seeing:

[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

Ian

---

### Post by -DomiNator- on 2005-03-12
Looks like your fglrx module isn't loaded, run lsmod in a console and see if fglrx is in the list, if not, try to load it with modprobe sudo modprobe fglrx

---

### Post by kubla on 2005-03-12
[QUOTE=-DomiNator-]Looks like your fglrx module isn't loaded, run lsmod in a console and see if fglrx is in the list, if not, try to load it with modprobe sudo modprobe fglrx[/QUOTE]
 
Thanks. You were right about the module not being loaded but the wierd thing is that the modprobe failed claiming the module wasn't there. I double-checked and it was in the right place:

/lib/modules/2.6.10-4-amd64-generic/kernel/drivers/video/

I recompiled the module from source, rebooted and all is right again... I'll have to check through my logs to see why it stopped loading before.

---

### Post by Pse on 2005-03-13
File corruption, perhaps?

---

