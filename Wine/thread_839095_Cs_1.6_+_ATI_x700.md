---
title: "Cs 1.6 + ATI x700"
date: 2008-06-24
forum: Wine
---

### Post by bugfish on 2008-06-24
Hello!

I ve got a problem to run cs 1.6. Installing Steam was no prob at all, but when i try to start couterstrike the desktop stays on the right side and counterstrike uses the left half of my screen. 
And the screen looks as if there are a lot of big (~10x10 mm) pixels. After each try i have to restart the X-Server. :frown:

My hardware:

Asus A6va notebook
1GB Ram
X700 mobility
80gb hdd (5400rpm)

And I'm usig kubuntu with KDE 4.0.5 on it!

fglrxinfo shows:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 2.1.7659 Release
```

fgl_glxgears:
```
mj@ubuntu:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
4106 frames in 5.0 seconds = 821.200 FPS
5559 frames in 5.0 seconds = 1111.800 FPS
5496 frames in 5.0 seconds = 1099.200 FPS
5678 frames in 5.0 seconds = 1135.600 FPS
5321 frames in 5.0 seconds = 1064.200 FPS
```

xorg.conf

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "de"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

#Section "Monitor"
#	Identifier   "Configured Monitor"
#EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

#Section "Device"
#	Identifier  "Configured Video Device"
#EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:3:0:0"
	Option	    "VideoOverlay"		"on"
	Option	    "OpenGLOverlay"		"off"
EndSection

#Section "Screen"
#	Identifier "Default Screen"
#	Device     "Configured Video Device"
#	Monitor    "Configured Monitor"
#EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

i hope someone can help me! :) 
and plz excuse my not really good english skills :roll:


update: in windowed mode i can play with about 10-15 fps :S but fullscreen doesnt works...

---

