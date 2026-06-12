---
title: "Need new color depth"
date: 2007-10-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by NFITC1 on 2007-10-03
I'm having trouble getting my color depth to change. I know I can change the Default in xorg.conf, which is currently at 24 (@1280x800), but when I try to change it to 16 or 32 nothing ever displays (from logon screen onward) although I can use the keyboard shortcuts to reboot. I'm using the ati drivers (Mobility Radeon 9700) and am wondering if that might be the problem.

fglrxinfo says:
```
~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 2.0.6849 Release
```

my current xorg.conf says (relevant parts only):
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Default Screen" 0 0
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

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
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

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "AIGLX" "off"
EndSection
```

Any Ideas?

---

### Post by jamesford on 2007-10-03
i thought 24 was the max depth

---

### Post by NFITC1 on 2007-10-04
Maybe for Ubuntu, but my Windows runs in 32-bit so I know my GFX card can handle it. Even so, why would it not be going into 16-bit mode? I've got a program that doesn't seem to want to work in 24-bit mode and I think changing it to either these will work for me.

---

### Post by Yellow Pasque on 2007-10-04
From the man page for xorg.conf:

> The range of depth values that are allowed depends on the driver. Most driver support 8, 15, 16 and 24. Some also support 1 and/or 4, and some may support other values (like 30). Note: depth means the number of bits in a pixel that are actually used to determine the pixel colour. **32 is not a valid depth value**. Most hardware that uses 32 bits per pixel only uses 24 of them to hold the colour information, which means that the colour depth is 24, not 32.

---

### Post by NFITC1 on 2007-10-04
Well, that's just dandy....
Anyway, why can I not get into 16-bit mode?

---

### Post by Yellow Pasque on 2007-10-04
I'm not sure why you can't change color depth to 16, unless it's unsupported for your model in the driver.

One thing that strikes me as odd is the AIGLX = true in your serverlayout section. The ATI driver doesn't support AIGLX at this time. I would comment out that line.

---

### Post by NFITC1 on 2007-10-04
I commented it out and erased what I will call "section 32", but I can't tell that it changed anything.

---

### Post by faical117 on 2007-11-13
thanks it work for me (32) !!!   :guitar:

---

