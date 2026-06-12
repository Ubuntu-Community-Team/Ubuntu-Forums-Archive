---
title: "Was fast, not very slow"
date: 2007-09-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by MetalAZ on 2007-09-10
I installed 7.04 64-bit on my desktop machine and it was running extremely fast.  I'm not sure what I did, but while trying to setup my second monitor I somehow managed to kill the speed.  Now it takes forever to open applications and using them is pretty much impossible.

System Monitor, when it's actually responding, is showing the only thing taking up CPU is itself at 50%.  I have it set to show all processes.

I've no idea how to start troubleshooting this since I can never see what's taking up the CPU, aside from System Monitor.

I'm using Gnome as my desktop and have the ATI video driver installed with fglrx (for use with compiz).  The problem exists both with and without compiz running.

Anyone have any suggestions as to where I can start looking to find the issue?

Any help would be greatly appreciated.

---

### Post by Jouke74 on 2007-09-11
Check the process with the command: "top" in a terminal. The process which is using most CPU is probably the one being nasty. Then try to figure out what you did to make this process start.

---

### Post by MetalAZ on 2007-09-11
That's showing just about no CPU usage.  

If I try to open something like a Terminal window, it takes forever and top shows 99% CPU usage by it the entire time.  Same with gedit and firefox.

---

### Post by rsambuca on 2007-09-11
You obviously messed up your xorg when trying to set up the dual monitors.  Perhaps you could post it here.

---

### Post by MetalAZ on 2007-09-11
Both monitors are working, but something is definitely screwed up.  I've been unable to get fglrx to work (not sure if it should work with two monitors).

Here's my xorg.conf

```


Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
  screen "aticonfig-Screen[1]" rightof "aticonfig-Screen[0]"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "Files"
	
	# path to defoma fonts
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[1]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	#Driver		"vesa"
	Option		"VideoOverlay"	"off"
	Option		"OpenGLOverlay"	"on"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[1]"
	Driver		"fglrx"
	#Driver	"vesa"
	Option		"VideoOverlay"	"off"
	Option		"OpenGLOverlay"	"on"
	Busid		"PCI:1:0:0"
	Screen	1
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SyncMaster"
	Defaultdepth	24
	Option		"AddRGBLXVisuals"	"true"
	Option		"DisableGLXRootClipping"	"true"
	SubSection "Display"
		Depth	1
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	Option		"AddRGBLXVisuals"	"true"
	Option		"DisableGLXRootClipping"	"true"
	SubSection "Display"
		Depth	1
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[1]"
	Device		"aticonfig-Device[1]"
	Monitor		"aticonfig-Monitor[1]"
	Defaultdepth	24
	Option		"AddRGBLXVisuals"	"true"
	Option		"DisableGLXRootClipping"	"true"
	SubSection "Display"
		Depth	1
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "ServerFlags"
	Option		"AIGLX"	"off"
EndSection

```

And here's the result of fglrxinfo

```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)



display: :0.0  screen: 1
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

I had to use the drivers through apt-get, not from ATI's site (those just gave me a black screen instead of the login screen).  I have an X1900 video card.

ATI driver is checked in the restricted drivers manager.

---

### Post by rsambuca on 2007-09-11
Oh, sorry.  I am an nvidia guy here, so I can't help you out with this one.  I still think it is likely that something in your xorg isn't quite right, though.

---

### Post by MetalAZ on 2007-09-11
No problem.  Maybe the new drivers that are coming out this week will fix it.

---

### Post by jocko on 2007-09-12
Check if there are any errors in /var/logXorg.0.log:
```
cat /var/log/Xorg.0.log | grep EE
```
Another thing: are you running normal Xorg, or have you set up an Xgl session?

---

### Post by Jouke74 on 2007-09-12
Hmmm. You aren't using the ATI driver now, but the Mesa (standard Vesa) driver instead. It will for certain slow things down a bit, but I don't think that much. 

Also there are three screens & monitors in your xorg.conf... I think that is the major problem causer.

---

### Post by MetalAZ on 2007-09-12
I was running in a normal Gnome session, not xgl.  I removed the xorg fglrx driver using apt-get and replaced my xorg.conf with a backup version, but the problem persists (even tried rebooting after).

My xorg.conf looks like this now:

```

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Loading that in gedit right now took forever.  It showed gconfd-2 as using 100% CPU.

Also I noticed that if I open up an image and zoom in so it fills the screen I see refresh issues... ripple effects.  Moving it around causing the same problem.  In the Screen Resolution tool it shows that I'm at 60 refresh (same as it was in Windows XP).  I'm at 1600x1200.

That extra display was the result of running aticonfig :( I only have one in there now but I'm having the same problem.

---

### Post by kuja on 2007-09-13
> **MetalAZ said:**
> I was running in a normal Gnome session, not xgl.  I removed the xorg fglrx driver using apt-get and replaced my xorg.conf with a backup version, but the problem persists (even tried rebooting after).

My xorg.conf looks like this now:

```

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Loading that in gedit right now took forever.  It showed gconfd-2 as using 100% CPU.

Also I noticed that if I open up an image and zoom in so it fills the screen I see refresh issues... ripple effects.  Moving it around causing the same problem.  In the Screen Resolution tool it shows that I'm at 60 refresh (same as it was in Windows XP).  I'm at 1600x1200.

That extra display was the result of running aticonfig :( I only have one in there now but I'm having the same problem.

You're still using the vesa driver. The vesa driver is somewhere between slow and dead slow and is pretty much never the optimal solution. That would explain the "ripple effects" as your cpu is probably doing much of your graphics cards job.

---

### Post by MetalAZ on 2007-09-13
I had put it back the way it was originally.  For some reason specifying ati never worked, it kept saying it couldn't find any screens.

What I did notice between all of the xorg.conf modifications is that when I ran gnome as root it was fast, no problems at all.

Last night I picked up a GeForce 8800 GTS video card hoping it would solve all of my problems, but unfortunately it didn't (probably my fault though).  I will be posting a thread about it in the "Multimedia & Video" area since I haven't the solution yet.

---

### Post by kuja on 2007-09-13
awww, I want one  :D

To get your nvidia card up 'n runnin', run "sudo apt-get install nvidia-glx-new && sudo nvidia-xconfig"

then, when you get to the gui, presuming you get to the gui, run "sudo nvidia-settings" to configure it for multiple monitors.

---

