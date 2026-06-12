---
title: "Strange display issue with fullscreen games using nVidia's TwinView"
date: 2006-01-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jave27 on 2006-01-10
This is reallly a minor issue, but an issue nonetheless...  I have a dual-monitor setup using nVidia's TwinView option.  After I figured out the MetaModes option in the xorg.conf file, I was able to get only a single screen to display games in fullscreen mode, however, when the game starts, the following happens:
[LIST]
[*]One screen blanks out (the correct action since I used NULL for it's mode)
[*]The other screen shows about half of the game on the right-hand side, and on the left-side I can still see Gnome.
[*]When I move the mouse to the right edge of the screen, the screen keeps scrolling over until the game is finally full screen and I can no longer see the Gnome menu or anything (I get the "correct" display, but it should theoretically pop up automatically without having to scroll over).
[/LIST]

I am getting this behavior with both [LinCity-NG]("http://lincity-ng.berlios.de/") (compiled from source since it's not available in breezy yet) and [Pingus]("http://pingus.seul.org") (SVN version also compiled from source).  Both can either use OpenGL mode or SDL mode, and the behavior is the same in both modes, so I've concluded it's an X.org issue or an nVidia issue.

System Specs:

AMD64 3400+
Asus A8V Deluxe Motherboard
XFX nVidia GeForce 6600GT
running Ubuntu Breezy AMD64.

Here's my xorg.conf file:

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
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
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
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"		"7"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"nv1"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"		"1"
	Option		"TwinView"		"yes"
	Option		"MetaModes"		"1152x864,1152x864; NULL,1152x864; NULL,1024x768; NULL,800x600; NULL,640x480"
	Option		"TwinViewOrientation"	"LeftOf"
	Option		"SecondMonitorHorizSync"	"30-80"
	Option		"SecondMonitorVertRefresh"	"50-120"
EndSection

Section "Monitor"
	Identifier	"LeftMonitor"
	Option		"DPMS"
	HorizSync	30-80
	VertRefresh	50-120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nv1"
	Monitor		"LeftMonitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
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
```

---

### Post by sjoerd222 on 2006-10-10
Hi

I got a similar problem. But I cannot scroll to a "correct view" I see only the left part of my application.

Here my xorg.conf
> 
# Xorg configuration created by system-config-display

Section "ServerLayout"
	Identifier     "single head configuration"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"

# Multiple FontPath entries are allowed (they are concatenated together)
# By default, a font server independent of the X server is
# used to render fonts.
	ModulePath   "/usr/lib64/xorg/modules/extensions/nvidia"
	ModulePath   "/usr/lib64/xorg/modules"
	FontPath     "unix/:7100"
EndSection

Section "Module"
	Load  "dbe"
	Load  "extmod"
	Load  "fbdevhw"
	Load  "record"
	Load  "freetype"
	Load  "type1"
	Load  "glx"
EndSection

Section "InputDevice"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#	Option	"Xleds"		"1 2 3"
# To disable the XKEYBOARD extension, uncomment XkbDisable.
#	Option	"XkbDisable"
# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#	Option	"XkbModel"	"pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#	Option	"XkbModel"	"microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#	Option	"XkbLayout"	"de"
# or:
#	Option	"XkbLayout"	"de"
#	Option	"XkbVariant"	"nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#	Option	"XkbOptions"	"ctrl:swapcaps"
# Or if you just want both to be control, use:
#	Option	"XkbOptions"	"ctrl:nocaps"
#
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "ch"
	Option	    "XkbVariant" "de_nodeadkeys"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "IMPS/2"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "yes"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Packard Bell 3020"
	HorizSync    30.0 - 65.0
	VertRefresh  50.0 - 90.0
	Option	    "dpms"
	DisplaySize 1000 400
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "nvidia"
	VendorName  "Videocard vendor"
	BoardName   "NVIDIA GeForce FX (generic)"
	Option      "NoLogo" "1"
	Option	    "nvidia"
	Option	    "DPMS"
	Option	    "TwinView" "on"
	Option	    "Xinerama" "on"
	Option	    "SecondMonitorHorizSync" "30-48"
	Option	    "SecondMonitorVertRefresh" "40-70"
	Option	    "TwinViewOrientation" "LeftOf"
	Option	    "MetaModes" "1280x1024, 1024x768; 1280x1024, NULL; 1024x768, NULL; 800x600, NULL"
	Option	    "ConnectedMonitor" "crt,crt"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes    "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024"
	EndSubSection
EndSection

Section "DRI"
	Group        0
	Mode         0666
EndSection



THX if anybody knows a solution how to get my application running so that i see what I'm doing

---

### Post by swedishlf on 2008-01-25
Is it better to dig up an old thread or start a new?  Well at any rate, here we are.

I'm having the exact same problem listed above with Gutsy amd_64, compiz, gnome, and twinview.  When I try running a game in full screen (or a qemu session for that matter) the second screen blanks, the app starts up and appears about halfway off the right hand side of the main screen.

I can scroll over so the window is approximately centered at which point it seems to lock in place.  The problem is that I also run into some mouse glitches.  The mouse seems to hit an invisible wall near the edges of the screen sometimes, but if I build up momentum I can sometimes make it past.  The mouse is also completely nonfunctioning in nexuiz.

Everything else is functioning fine, I've tried it with and without compiz running, makes no difference.

xorg:
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Fri Jan 11 14:27:25 PST 2008

Section "ServerLayout"
        Identifier      "Layout0"
  screen 0 "Screen0" 0 0
        Inputdevice     "Keyboard0"     "CoreKeyboard"
        Inputdevice     "Mouse0"        "CorePointer"
EndSection

Section "Files"
        Rgbpath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
        Load            "dbe"
        Load            "extmod"
        Load            "type1"
        Load            "freetype"
        Load            "glx"
EndSection

Section "ServerFlags"
        Option          "Xinerama"      "0"
EndSection

Section "InputDevice"
        # generated from default
        Identifier      "Mouse0"
        Driver          "mouse"
        Option          "Protocol"      "auto"
        Option          "Device"        "/dev/psaux"
        Option          "Emulate3Buttons"       "no"
        Option          "ZAxisMapping"  "4 5"
EndSection

Section "InputDevice"
        # generated from default
        Identifier      "Keyboard0"
        Driver          "kbd"
EndSection

Section "Monitor"
        # HorizSync source: edid, VertRefresh source: edid
        Identifier      "Monitor0"
        Vendorname      "Unknown"
        Modelname       "Proview"
        Horizsync       30.0    -       80.0
        Vertrefresh     60.0    -       75.0
        Option          "DPMS"
EndSection

Section "Device"
        Identifier      "Videocard0"
        Driver          "nvidia"
        Vendorname      "NVIDIA Corporation"
        Boardname       "GeForce 8600 GT"
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Videocard0"
        Monitor         "Monitor0"
        Defaultdepth    24
        Option          "TwinView"      "1"
        Option          "TwinViewXineramaInfoOrder"     "CRT-0"
        Option          "metamodes"     "CRT-0: nvidia-auto-select +1024+0, CRT-1: 1024x768 +0+0;1440x900,NULL;1024x768,NULL;800x600,NULL;640x480,NULL"
        Option          "AddARGBGLXVisuals"     "True"
        SubSection "Display"
                Depth   24
        EndSubSection
EndSection

Section "Extensions"
        Option          "Composite"     "Enable"
EndSection

```

Any help is greatly appreciated!

---

### Post by OliW on 2008-01-26
Open nvidia-settings as root, go to the "X Server Display Configuration" page, select your left-hand screen and click the checkbox at the bottom of the page saying "Make this the promary display for the X screen". Save to config. Restart X.

You'll probably have to juggle all your panels around now.

Now fullscreen games will open across both screens still, but your screens will be the correct way around, so you can at least see what's going on.

==================

On top of that, you can add additional "metamodes" to your config (as some of you have done), but I definitely suggest setting your screens up correctly (as above) first.

---

### Post by swedishlf on 2008-01-26
Thanks for the tip, that definitely fixes the problem.  But the screen I prefer as primary is on the right.  Is there any way to tell it to present the login screen there?  Should I be able to move my panels back to that screen?  As you suggested the case would be, my panels all moved to the left screen after implementing your suggestion.

These are issues I can probably deal with though.  The larger problem has been solve.  Thanks!

---

### Post by OliW on 2008-01-26
Panels: you can just drag these around. If they start causing you real issues (by expanding to fill the entire 2 screens), drag them all to the side of one screen, log out and in again, then put them where you want them.

Login screen: I think it always picks the default screen. I've just had a look around for a setting but I can't find it. Perhaps somebody else knows ...

---

### Post by swedishlf on 2008-01-26
That's worked like a champ.  I can certainly deal with the login screen issue, and if I find a solution I'll post it.

Here's the new working xorg.conf:
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Fri Jan 11 14:27:25 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Proview"
    HorizSync       30.0 - 80.0
    VertRefresh     60.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "CRT-0: nvidia-auto-select +1024+0, CRT-1: 1024x768 +0+0; 1440x900,null;1024x768,null;800x600,null;640x480,null;320x240,null"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Thanks so much!

---

### Post by llcawthorne on 2008-01-27
The TwinViewXineramaInfoOrder option should control which monitor displays your login screen.  I had to use:

Option "TwinViewXineramaInfoOrder" "DFP,CRT-0"

to move the login from my tv to my flat panel.  You already seem to have the option there, so maybe changing it to "CRT-0" or "CRT-0, CRT-1" or "CRT-1, CRT-0" or something like that might help.

---

### Post by swedishlf on 2008-01-27
changing:
Option "TwinViewXineramaInfoOrder" "DFP,CRT-1"
to

Option "TwinViewXineramaInfoOrder" "DFP,CRT-0"

Does indeed put the login screen back to the main panel, but it also reinstates the initial scrolling window problems.  I think perhaps the TwinViewXineramaInfoOrder value sets the "primary desktop?"

---

### Post by llcawthorne on 2008-01-27
Ah, yes.  I believe it does.  I suppose that it is assumed that you want to login on your "primary desktop."

---

