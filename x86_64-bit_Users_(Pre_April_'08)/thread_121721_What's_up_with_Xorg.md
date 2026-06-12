---
title: "What's up with Xorg?"
date: 2006-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by andrewsawyer on 2006-01-25
Heya,

I hope someone can help me fix a problem that has been driving me mad.  My xorg is running at upto 92% CPU usage.  After a reboot, it will sit at <14% for half an hour or so, and then creep up.  My xorg.conf is below:

```
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
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
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
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	VendorName 	"Videocard vendor"
	BoardName 	"NVIDIA GeForce 6600 GT"
	Option		"ConnectedMonitor" "CRT, DFP"
#        Option          "RenderAccel"           "true"
#        Option          "AllowGLXWithComposite" "true" 
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
	Modeline	"1440x900@65" 83.91 1280 1312 1624 1656 800 816 824 841
	Option		"TwinView" "true"
	Option		"TwinViewOrientation" "RightOf"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Option		"MetaModes" "1440x900,1280x1024;1280x1024,1280x1024;1280x768,1024x768;1280x768,NULL;1024x768,NULL;NULL,1280x1024"
		Option     	"SecondMonitorHorizSync"   "30-82"
    		Option     	"SecondMonitorVertRefresh" "56-76"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

Section "ServerFlags"
    Option      "Xinerama"      "false"
EndSection

#Section "Extensions"
#	Option		"Composite"	"Enable"
#EndSection
```

I'm running a twin monitor setup, and I tried Poofyhairguy's guide for getting the KDE composite manager working: [http://ubuntuforums.org/showthread.php?t=115974](http://ubuntuforums.org/showthread.php?t=115974).  The problem seemed to start after this, however as far as I'm aware, I have fully restored the system to it's original settings and removed any programs that I installed for the How-to.

My default.session file is as follows:

```
[Default]
num_clients=8
0,id=default0
0,Priority=10
0,RestartCommand=gnome-wm --sm-client-id default0
1,id=default1
1,Priority=40
1,RestartCommand=gnome-panel --sm-client-id default1
2,id=default2
2,Priority=40
2,RestartCommand=nautilus --no-default-window --sm-client-id default2
3,id=default3
3,Priority=60
3,RestartCommand=gnome-cups-icon --sm-client-id default3
4,id=default4
4,Priority=40
4,RestartCommand=gnome-volume-manager --sm-client-id default4
5,id=default5
5,Priority=40
5,RestartCommand=magicdev --sm-client-id default5
6,id=default6
6,Priority=50
6,RestartCommand=vino-session --sm-client-id default6
7,id=default7
7,Priority=50
7,RestartCommand=update-notifier --sm-client-id default7
```

And I am have replaced Metacity with xfwm4, however I don't have any of the drop shadows running.

If someone could give me some suggestions, it'd be very much appreciated.

Thank you in advance,

Andy

---

