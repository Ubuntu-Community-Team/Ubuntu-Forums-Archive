---
title: "synaptics touchpad driver issue"
date: 2006-09-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by chrishack14 on 2006-09-08
Hello,

Today, I have been trying to set up Kubuntu Dapper 64-bit on my new HP dv2000z laptop and have nearly everything working, except a couple features of my synaptics touchpad.  Neither the scrollbar on the left side of the touchpad nor the "tap-and-drag" feature will work.  Well, actually the scrollbar does work, but only with the xorg-driver-synaptics driver that is installed by default in Dapper, but that has all sorts of bugs that caused the pointer to go berserk.  Therefore, I compiled and installed the latest driver, and now the mouse is usable, but those two features won't work.  I tried changing some settings in the xorg.conf file, but these did not help at all.  I find this very strange, since I have an older AMD64 laptop with Dapper installed and the same driver, and it worked just fine after going through exactly the same steps.  The relevant sections of my xorg.conf file read:

```

Section "Module"
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
	Load	"synaptics"
EndSection

...

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"on"
EndSection

...

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

```

Does anyone else have this laptop, and if so, have you had similar problems?  Any ideas?

Thanks!

---

### Post by chiefofthejojos on 2006-12-15
Hi, did you ever figure out the touchpad?  I'm using the same laptop, and the touchpad is driving me crazy!  I'm using Ubuntu Dapper with the built in synaptic driver and it's almost perfect, except that whenever I try to move the mouse it thinks I'm clicking!  So it's always dragging stuff all over when I don't want to.  Isn't there a way to reduce the sensitivity or something?  Maybe I should try the new synaptics driver.  I've downloaded and compiled 0.14.6, but I'm slightly scared to install it.  Do I just "sudo make install" or do I need to copy the driver to a special location.  Because in the INSTALL file it says it will copy it to /usr/X11R6/lib/modules/input/ but that directory doesn't exist on my installation.

---

### Post by DarkN00b on 2006-12-15
I'm running an HP ze2000 laptop with the Synaptics touchpad. Mine works perfectly. Here's my Synaptics section in xorg.conf :

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection
```

The only difference I see is that you have one more line than me:

```
	Option		"SHMConfig"		"on"
```

You could try commenting out that line and restarting [ctrl+alt+bkspc] to see if that helps. To comment a line out, just place a # at the beginning of the line.

---

