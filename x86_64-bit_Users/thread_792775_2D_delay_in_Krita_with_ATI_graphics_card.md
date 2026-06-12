---
title: "2D delay in Krita with ATI graphics card"
date: 2008-05-13
forum: x86 64-bit Users
---

### Post by DrowningNixis on 2008-05-13
I am running Hardy Heron, 64bit with a ATI Radeon X1600.  I installed the lastest binary drivers from ATI.  I am noticing a slight delay in Krita with my mouse and a huge delay with my wacom tablet.  I do not experience this in Inkscape, Gimp or any other use (desktop, firefox, etc.)  Originally the VideoOverlay was on and the OpenGLOverlay was off, but after switching it, I saw an improvement.

Below is the pertinent sections of my xorg.conf:

> Section "Module"
        Load    "Glcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fglrx"
        Option          "VideoOverlay"  "off"
        Option          "OpenGLOverlay" "on"
        Option          "AGPMode" "4"
        Option          "AGPFastWrite" "yes"
        Option          "EnablePageFlip" "on"
        Option          "RenderAccel" "on"
        Option          "AccelMethod"   "EXA" # or XXA
#     Option            "BackingStore" "true"
#     Option            "ExaNoOffscreenPixmaps"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

Section "Extensions"
        Option          "Composite"     "Disable"
EndSection

Section "DRI"
        Mode            0666
EndSection

---

