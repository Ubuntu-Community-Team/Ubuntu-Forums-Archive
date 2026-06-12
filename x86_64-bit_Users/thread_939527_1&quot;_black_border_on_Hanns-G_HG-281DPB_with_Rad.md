---
title: "1&quot; black border on Hanns-G HG-281DPB with Radeon 2600HD"
date: 2008-10-06
forum: x86 64-bit Users
---

### Post by stitchedwings on 2008-10-06
Hello.

I am using Xubuntu 8.04...  I am having a problem where I get a 1" black border with a Hanns-G HG-281DPB with resolution at 1920x1200 from an ATI Radeon 2600HD HDMI.

If anyone knows how to get the viewable area to stretch over the entire screen at this resolution, please let me know.


Here is my /etc/X11/xorg.conf:

TIA!

-----------------------------

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
        Option         "Xinerama" "1"
        Option         "Clone"    "off"
EndSection

Section "Module"
# This loads the font modules
# This loads the GLX module
        Load  "dbe"     # Double buffer extension
        SubSection "extmod"
                Option      "omit xfree86-dga"   # don't initialise the DGA ext$
        EndSubSection
        Load  "type1"
        Load  "freetype"
    #Load        "speedo"
        Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection


Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes "1920x1200"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes "1680x1050"
	EndSubSection
EndSection

---

