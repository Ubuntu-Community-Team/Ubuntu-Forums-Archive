---
title: "Problems with video (not consistant?)"
date: 2007-09-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by NFITC1 on 2007-09-26
OK, so I'm new to this board although I have read several articles on it and gotten good help from it. I'm having a problem with getting my 64-bit Feisty working on my laptop with a Mobility Radeon 9700. I've tried the Mesa drivers and the ATI drivers. The Mesa drivers don't seem to have a compatible libGL.so with whatever I have because everything I have attempted to compile has said
"skipping incompatible /usr/lib/include/libGL.so for -lGL"
or something real close to that.

Until recently, every time I've run glxinfo or fglrxinfo or any of their derivatives, it lists the driver as Mesa DRI Indirect. This is not good since this means that my rendering is inactive or the drivers are not initialized. I just this morning changed my xorg.conf to use the "ati" drivers instead of the "fglrx" drivers. Now glxinfo reports a "Mesa AGP 1 mode" or something like that, which is CLOSER to what I want, but the libGL.so is still not compatible. Also this screws up my desktop something awful. The native res of my laptop screen is 1280x800, but if I set it to that using the 3D-enabled drivers, nothing displays properly. There are random lines all over the screen and it makes the cursor not display properly (as if the desktop 3D render is incompatible with my drivers). But the desktop looks fine without these drivers.
Oddly, some OpenGL games work fine without these render drivers (Linux games like Super Tux and Tuxracer and such).
Anyway, is there a driver  that's specific to the 64-bit that works? I've seen pages that say to use the ATI driver and I've seen pages that say use the Mesa driver. Frankly, I don't care which one so long as it works.

---

### Post by NFITC1 on 2007-09-28
OK, so I've had a little more time to investigate the problem that I'm having. Turns out that I'm inadvertently using the Mesa display drivers when I want to be using the fglrx. I want to use the ATI drivers, but I'm using X 7.2.0.

My fglrxinfo gives me this:
```
~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
```

Which is what I've come to realize that I don't want.
Worse still, xvinfo gives me this:
```
~$ xvinfo
X-Video Extension version 2.2
screen #0
```

Some relavent portions of xorg.conf:
```
Section "ServerLayout"
#     Screen      0  "aticonfig-Screen[0]" 0 0
	Identifier     "Default Layout"
	Screen      0  "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	Option	    "AIGLX" "true"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
#	Driver      "fglrx"
	Identifier  "aticonfig-Device[0]"
	Driver      "ati"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     32
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"

#	Device	   "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection
```

---

### Post by NFITC1 on 2007-09-29
As useful as this forum seems, I was able to solve my problem myself. I followed the instructions on [HTML]http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide[/HTML] about twice before it finally worked for me. Thus fglrxinfo happily reports:
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 2.0.6849 Release
```

Which makes ME happy.

---

