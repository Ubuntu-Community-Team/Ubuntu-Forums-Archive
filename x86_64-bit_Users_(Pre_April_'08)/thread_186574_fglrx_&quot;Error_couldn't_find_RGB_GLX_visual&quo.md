---
title: "fglrx: &quot;Error: couldn't find RGB GLX visual&quot;"
date: 2006-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by NyanNyanKoneko on 2006-06-02
First of all, I want to say that I love Dapper Drake so much!  This is easily the best, most polished version of Linux I have ever installed.  Everything about it is perfect: its low bloat, its speed, its new theme!  Thank you so much, everyone!

However, I am having some problems with 3D acceleration with my ATI Radeon 9600 XT.  I installed the fglrx drivers, and edited my xorg.conf to make use of the drivers, but when I run glxinfo or any OpenGL application, I get an error similar to this:

> :~$ glxinfo
name of display: :0.0
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None

I get the same error if I use the ati or radeon drivers.  Any ideas?

---

### Post by NyanNyanKoneko on 2006-06-02
I figured I should post my xorg.conf as I have it configured currently.  :)

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Primary Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "dbe" #double buffer extention.
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

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "A150-X2"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Radeon 9600 XT"
	Driver      "fglrx"
	Option       "no_accel" "no"
   	Option       "no_dri" "no"
   	Option       "DynamicClocks" "on"
   	Option       "mtrr" "on"
   	Option       "DesktopSetup" "Single"
   	Option       "ScreenOverlap" "0"
   	Option       "Capabilities" "0x00000000"
   	Option       "CapabilitiesEx" "0x00000000"
   	Option       "VideoOverlay" "on"
   	Option       "OpenGLOverlay" "off"
   	Option       "CenterMode" "off"
   	Option       "PseudoColorVisuals" "off"
   	Option       "Stereo" "off"
   	Option       "StereoSyncEnable" "1"
   	Option       "FSAAEnable" "no"
   	Option       "FSAAScale" "1"
   	Option       "FSAADisableGamma" "no"
   	Option       "FSAACustomizeMSPos" "no"
   	Option       "FSAAMSPosX0" "0.000000"
   	Option       "FSAAMSPosY0" "0.000000"
   	Option       "FSAAMSPosX1" "0.000000"
  	Option       "FSAAMSPosY1" "0.000000"
   	Option       "FSAAMSPosX2" "0.000000"
   	Option       "FSAAMSPosY2" "0.000000"
   	Option       "FSAAMSPosX3" "0.000000"
   	Option       "FSAAMSPosY3" "0.000000"
   	Option       "FSAAMSPosX4" "0.000000"
   	Option       "FSAAMSPosY4" "0.000000"
   	Option       "FSAAMSPosX5" "0.000000"
   	Option       "FSAAMSPosY5" "0.000000"
   	Option       "UseFastTLS" "0"
   	Option       "BlockSignalsOnLock" "on"
   	Option       "UseInternalAGPGART" "no"
   	Option       "ForceGenericCPU" "no"
   	Option       "KernelModuleParm" "agplock=0"
   	Option       "PowerState" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Primary Screen"
	Device     "Radeon 9600 XT"
	Monitor    "A150-X2"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection
```

---

### Post by Kilz on 2006-06-02
Did you follow this howto? [https://wiki.ubuntu.com/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2](https://wiki.ubuntu.com/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2)

---

