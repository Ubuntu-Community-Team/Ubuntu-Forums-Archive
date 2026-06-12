---
title: "ATI drivers"
date: 2005-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by mping on 2005-01-25
Can someone please tell me how to install ati drivers for amd64 arch? im kinda new to ubuntu... i tried reading the posts here but nothin works... myfglrxinf reads this:

OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.3 Mesa 4.0.4

and my XFreeconf file reads:
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"

I suppose the driver is installed, but im getting really low scores on glxgears for an ati 9600XT:
4107 frames in 5.0 seconds = 821.400 FPS
3840 frames in 5.0 seconds = 768.000 FPS
5760 frames in 5.0 seconds = 1152.000 FPS
5160 frames in 5.0 seconds = 1032.000 FPS
6600 frames in 5.0 seconds = 1320.000 FPS

on my prev gent2 machine (which i uninstalled to install ubuntu :) ) i had higher scores, and i had to switch opengl-interface with #>opengl-update ati to ati opengl interface. So i think the drivers are installed, but somethin's wrong...

i choose not to Sync buffer with refresh...

---

### Post by mping on 2005-01-26
Well it seems that i have solved it, more or less... just installed fglrx-kernel-source, it installed me the kernel module, lsmod shows me fglrx (id didnt before). It sounds stupid not to have previous installed the module, but the info box on synaptic says this:

> ATI binary kernel module source
This package builds the ATI XFree86 4.x/X.Org binary kernel module needed
by xorg-driver-fglrx/xfree86-driver-fglrx.  This package is not needed on an
Ubuntu system because a pre-compiled kernel module is supplied by the
linux-restricted-modules  packages.

Im still a bit confused, what module is this? i downloaded it from hoary, is this the drivers ati has on their site?

---

