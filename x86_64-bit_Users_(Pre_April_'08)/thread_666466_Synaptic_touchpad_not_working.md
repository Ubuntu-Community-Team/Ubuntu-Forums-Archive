---
title: "Synaptic touchpad not working"
date: 2008-01-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Zealous on 2008-01-13
Helo guys...
this is my very first post in this community. I have installed ubuntu 7.10 on my lenovo laptop Y500 series...my synaptics touchpad and keypad are not working properely..i searched on net a lot and i found some solutions and tried then it worked and i shut down my laptop...

then after sometime i again started my laptop then again it was not working it happened 2-3 times. i fix it and shut it down and after starting it doesn't work..

i have tried 
**SHMConifg "on"**

**synclient TouchpadOff=0 **

sometimes the above command work and then the touch pad also work but sometimes it says
[I]
can't access shared memory. SHMConfig disabled??[/I]

i use USB mouse and keyboard to do all this...

plz help i am not able to fix if forever

---

### Post by DFreeze on 2008-01-13
I've been searching for a solution to this (or a similar) problem as well. Haven't found it, so far. My mousepad never works, and I read somewhere that the newer kernels have problems with some mice and touchpads. I booted in PCLinuxOS (kernel 2.6.18) and there the touchpad works. In ubuntu (Feisty and Gutsy) I never got it going.

So I wish you good luck and I'll keep an eye out to this thread to see whether there is someone who can help us both...

---

### Post by cubicsilver on 2008-01-14
Just curious but could you post your xorg.conf

do you have this line:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"		"true"
EndSection
```

---

### Post by DFreeze on 2008-01-14
Yup, I have it:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
```

I just tried 'sudo cat /dev/psaux' to see whether it responds to movement of my touchpad, but that only responds to my usb-mouse. Strange, since my mouse is declared in Xorg.conf like this:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
```

Doing a 'sudo cat /dev/input/mice' does not react to either one, and /dev/input/mouse1 only responds to the usb-mouse.

---

### Post by Zealous on 2008-01-15
well my problem has been solved:)
my problem was a little bit different....when i do the "SHMConfi" "on" thing my touchpad and keypad starts working and when i shut down my lappy and restart it then it was not working....

but later i found that there was some special problem with my Lenovo y500 series laptop..one of my friends googled and fixed it up...the solution was in some other form of this community....

you can google with keyworkd "Lenovo Y500 ubuntu" this first link to this community will take u to the solution...
now my touchpad and keypad is working fine....
thanks to my friend and thanks to all here

---

