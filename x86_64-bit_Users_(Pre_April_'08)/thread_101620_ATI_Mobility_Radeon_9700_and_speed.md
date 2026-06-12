---
title: "ATI Mobility Radeon 9700 and speed"
date: 2005-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by sammal on 2005-12-10
Hello,

I have installed the latest proprietary driver from ATI according to instructions found elsewhere in this forum. When I run glxinfo it shows that
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
And xserver log also shows the radeon driver loading without errors:

(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x00000001
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled

 However the speed I get from my display driver is exactly the same as with software rendering, glxgears is really slow etc. Any ideas?

My xorg.conf Modules section looks like

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
#       Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

I know these similar issues are handled in this forum really often and I'm sorry if I missed one handling this exact thing.

Cheers, 
Lasse

---

