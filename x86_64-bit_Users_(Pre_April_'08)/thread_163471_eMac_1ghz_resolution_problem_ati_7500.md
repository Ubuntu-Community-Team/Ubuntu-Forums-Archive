---
title: "eMac 1ghz resolution problem ati 7500"
date: 2006-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by jamessp007 on 2006-04-20
I have installed and have been running my emac at the 1024x768 @ 89hz.  This setting is too big.  
Graphical tools for changing resolution is locked to the 1024x768 setting. 
Manual config crashes xserver.    Can anyone please help fix this?

xorg.conf appears as follows:

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 7500 (RV200 QW)"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"iMac"
	Option		"DPMS"
	HorizSync	71-73
	VertRefresh	70-140
	Modeline "1280x960_75.00" 129.86 1280 1368 1504 1728 960 961 964 1002 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 7500 (RV200 QW)"
	Monitor		"iMac"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

