---
title: "[SOLVED] Warcraft/ATI video boxy"
date: 2008-06-24
forum: Wine
---

### Post by soulcmdc on 2008-06-24
So I'm stumped as to what's wrong with my setup for playing WoW. I have an ATI x1600, installed the latest drivers (8.50.3) and believe they're working properly (glxgears runs ~5k frames/s).  I've followed every guide for getting WoW to work (and it worked fine on my laptop - thought that's an Intel chipset)

My setup is ATI x1600, AMD 64, Hardy 32-bit, Wine 1.0.
Followed the OpenGL registry edit, even tried re-installing wine
fglrxinfo tells me:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.1.7659 Release

```

$glxinfo | grep rendering
direct rendering: Yes

Once the game starts, my video is screwed until I restart the Xserver.  If I take a screenshot, it appears all is well.  Attatched is a physical picture of the screen.

---

### Post by soulcmdc on 2008-06-24
Here's my current X11 layout, if this is of any help. Thank you!
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
      Fontpath "/usr/share/fonts/X11/misc"
      Fontpath "/usr/share/fonts/X11/cyrillic"
      Fontpath "/usr/share/fonts/X11/100dpi/:unscaled"
      Fontpath "/usr/share/fonts/X11/75dpi/:unscaled"
      Fontpath "/usr/share/fonts/X11/Type1"
      Fontpath "/usr/share/fonts/X11/100dpi"
      Fontpath "/usr/share/fonts/X11/75dpi"
      Fontpath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection
      
Section "Module"
   Load     "i2c"
   Load     "bitmap"
   Load     "ddc"
   Load     "dri"
   Load     "extmod"
   Load     "freetype"
   Load     "glx"
   Load     "GLcore"
   Load     "int10"
   Load     "vbe"
EndSection

Section "ServerFlags"
   Option      "AIGLX"  "off"
EndSection


Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
   Option      "VideoOverlay" "on"
   Option      "OpenGLOverlay"   "off"
   Option      "DynamicClocks" "on"
   Option      "Capabilities" "0x00000800"
   Option      "UseFastTLS" "off"
   Option      "KernelModuleParm" "locked-userpages=0"
EndSection

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

Section "DRI"
   Mode  0666
EndSection

Section "Extensions"
   Option   "Composite" "Disable"
   Option   "Composite" "0"
EndSection

```

---

### Post by soulcmdc on 2008-06-26
This is simply a bug in the 8.6 drivers - download 8.5 here: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-5-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-5-x86.x86_64.run) and all should be well again.

---

