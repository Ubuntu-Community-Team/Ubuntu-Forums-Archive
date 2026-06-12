---
title: "Kubuntu 8.04 64, no audio :("
date: 2008-04-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by LK_gandalf_ on 2008-04-21
Hi, I've just installed Kubuntu 8.04 RC 64bit on my laptop,  Dell Xps M1530, after some month using the 32bit,
I'm very happy seeing that now some old "problems" are fixed. flash player is in the repository, skype is installed with 4 easy commands in the shell, amarok take its mp3 support withour problem. 

I have a problem with my touchpad, it is completely crazy. If I only touch it, the cursor goes everywhere cliccking everything, for some seconds. 
Please, can you help me fixing this? Or, if it is not possible to fix it, just to know what to report as a bug.

I don't know how to find information about the touchpad.Maybe the info in the xorg.conf file could be useful:

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection


```

Thank you

---

### Post by LK_gandalf_ on 2008-04-21
Up. 
Please note I've changed the content of this topic. it's not about audio problem, but touchpad. 
may a moderator change the topic title, please? tnx

---

### Post by LK_gandalf_ on 2008-04-25
up....this is quote disturbing. :(

---

