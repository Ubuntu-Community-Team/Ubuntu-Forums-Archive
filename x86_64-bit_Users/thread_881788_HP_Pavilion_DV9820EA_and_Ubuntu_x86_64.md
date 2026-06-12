---
title: "HP Pavilion DV9820EA and Ubuntu x86_64"
date: 2008-08-06
forum: x86 64-bit Users
---

### Post by Uzelth on 2008-08-06
Heya,

I recently installed Ubuntu x86_64 on my new HP Pavilion DV9820EA... The majority of things work out the box... I got the nVidia drivers sorted... Wireless works fine with injection patch.

However I'm having a couple of problems:

[list]
[*]The mouse... If I use the lock button then unlock a help browser appears.
[*]Screen brightness... I have to keep setting the brightness up every time I login
[*]GSynaptics won't run - says it needs "SHMConfig" set to "true" in xorg.conf (which it is, see below):
```
Section "InputDevice"
	Identifier	"Mouse[0]"
	Driver		"mouse"
	Option		"Protocol"			"auto"
	Option		"Device"			"/dev/psaux"
	Option		"Emulate3Buttons"		"no"
	Option		"ZAxisMapping"			"4 5"
EndSection

Section "InputDevice"
	Identifier	"Touchpad[0]"
	Driver		"mouse"
	Option		"Protocol"			"synaptics"
	Option		"Device"			"/dev/psaux"
	Option		"Emulate3Buttons"		"no"
	Option		"ZAxisMapping"			"4 5"
	Option		"SHMConfig"			"true"
EndSection
```
[/list]

I think that's it for the moment... I'll post a reply if I remember anything else.

If anyone could help, I'd be very grateful :)

---

### Post by Yellow Pasque on 2008-08-06
Change it to 
```
Option "SHMConfig" "on"
```
[https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig](https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig)

---

### Post by Uzelth on 2008-08-08
I've noticed another problem... I compiled the drivers for linux-uvc from svn... The webcam works in Cheese, but not with flash or on aMSN... Any ideas why this might be?

---

