---
title: "dual screen"
date: 2007-06-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sipheren on 2007-06-15
Hey,

Just a couple of questions, I have set up dual screen using "Big Desktop" and its working, only problem is I have to move the mouse to the bottom of my main screen to get to the second monitor and to get back I have to move to the left side of the second monitor.
I have the second monitor to my right and would like it to work like that.

Also my fan keeps going into full speed, then normal speed, then full speed. Its a little annoying, any ideas on how to stop it?

Cheers

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Screen      1  "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Radeon X1950pro"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Radeon X1950pro"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1600x1200"
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

### Post by Sipheren on 2007-06-18
anyone??

---

