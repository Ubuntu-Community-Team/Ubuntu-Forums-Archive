---
title: "How do i enable compiz?"
date: 2008-01-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by darkenemy on 2008-01-14
i have done everything to install the ati driver for my Radeon HD 2600 XT card
ATI Catalyst works fine
restricted drivers manager says that the driver is enabled
screen and graphics has fglrx working

but no compiz............

when i try to enable it via appearance it doesn't work
when i do the old ALT+F2 and "compiz --replace" it doesn't go either

something strange did happen when i went through the shoot and miss of trying to install the ati driver... my xorg.conf file was replaced with like 10 different ones with names like xorg.conf.1 and xorg.conf.fglrx.... i dont know why but maybe this is the problem

teh output of fglrxinfo is

```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2600 XT
OpenGL version string: 2.1.7170 Release

```

also, i have attached a picture of all the variations of th xorg.conf files in etc/X11

the one labeled simply xorg.conf has this inside

```

# Fallback X.org config file
# FIXME: include the wacom devices (would only add noise at the current
#        development stage)

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"GLcore"
	Load		"glx"
	Load		"dbe"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:5:0:0"
	Driver		"fglrx"
	Screen	0
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```

attached is a picture of my X11 folder




can anyone help me enable compiz?

---

### Post by Yellow Pasque on 2008-01-14
I think you need an option to enable the Composite extension in there somewhere. Also make sure fglrx is added to the WHITELIST="" line in /usr/bin/compiz You can then enable them under one of the tabs in the Appearance prefs.

BTW, the other files xorg.confs won't affect anything and you can remove them if you're done with them.

---

### Post by darkenemy on 2008-01-16
i erased everything else under whitelist and put "fglrx"  but it didnt do anything...

---

### Post by darkenemy on 2008-01-16
strange, i typed

compiz whatzit


into the terminal and somehow it fixed everything

---

