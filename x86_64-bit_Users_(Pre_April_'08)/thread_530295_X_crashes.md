---
title: "X crashes"
date: 2007-08-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by period3 on 2007-08-20
I'm having problems with X crashes: maybe once a day or so.  This is extremely annoying: I was running a process that takes about 12 hours to complete, and X just crashed about 10 hours in :(  (flicks off and brings up the login screen) .   

Ubuntu Feisty
Core 2 Duo, Asus P5K-VM (G33 chipset), integrated video
4 GB memory
vesa driver (couldn't get intel driver working, don't really care about video performance.)

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x6d) [0x48282d]
1: /lib/libc.so.6 [0x2b9d823e3d40]
2: /usr/lib/xorg/modules/extensions//libGLcore.so(xmesa_check_and_update_buffer_size+0xc) [0x2b9d861e363c]
3: /usr/lib/xorg/modules/extensions//libGLcore.so [0x2b9d861e2b3d]
4: /usr/lib/xorg/modules/extensions//libglx.so [0x2b9d83cc7d6b]
5: /usr/X11R6/bin/X(compPositionWindow+0x62) [0x4b0592]
6: /usr/X11R6/bin/X(ResizeChildrenWinSize+0x168) [0x43cdb8]
7: /usr/X11R6/bin/X(ReparentWindow+0x1cc) [0x43d01c]
8: /usr/X11R6/bin/X(ProcReparentWindow+0xbc) [0x44d9cc]
9: /usr/X11R6/bin/X(Dispatch+0x1cb) [0x44df4b]
10: /usr/X11R6/bin/X(main+0x45d) [0x43703d]
11: /lib/libc.so.6(__libc_start_main+0xf4) [0x2b9d823d08e4]
12: /usr/X11R6/bin/X(FontFileCompleteXLFD+0x241) [0x436339]

Fatal server error:
Caught signal 11.  Server aborting

---

