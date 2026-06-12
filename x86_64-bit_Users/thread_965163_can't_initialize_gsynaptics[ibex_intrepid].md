---
title: "can't initialize gsynaptics[ibex intrepid]"
date: 2008-10-31
forum: x86 64-bit Users
---

### Post by bAsem on 2008-10-31
i know this has been posted 1 million times .. but i looked thru them and they all say that u have to add a single line "shmconfig" "true" under input devices "synaptics touchpad"

but here is my xorg.conf after installing nvidia drivers 177 on the new ibex intrepid 


```
 Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

---

### Post by bAsem on 2008-10-31
i just wanted to change my left mouse button on the touchpad to middle mouse button .. 

i think nvidia changed the xorg.conf file and i dun want to mess with it coz i really dont want it to crash the x-server

---

### Post by ChaoticMind on 2008-11-02
I'm having the same problem as well..

---

### Post by bAsem on 2008-11-02
well i found an alternate way to make middle click . dunno if u know about it or not ... 

if u press the left and right mouse buttons together in the same time it will produce a middle .. 

until some ubuntu guru helps us this will have to do :)

---

### Post by ChaoticMind on 2008-11-02
hehe, good... 

I actually use gsynaptics for the circular scroll which i find very convenient...

---

### Post by bAsem on 2008-11-02
well i would like to use that too .. if someone would guide me thru the editing of the xorg.conf file

---

### Post by TitoPoli on 2008-11-04
You have to add this two sections in your xorg.conf

```
Section "InputDevice"
        Identifier "Synaptics Touchpad"
        Driver "synaptics"
        Option "SendCoreEvents" "true"
        Option "Device" "/dev/psaux"
        Option "Protocol" "auto-dev"
        Option "HorizScrollDelta" "0"
        Option "SHMConfig" "true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```
Then restart xserver and run gsynaptics.

---

### Post by Tweak42 on 2008-11-04
I was thrown off by the empty xorg.conf file too.  Apparently ibex uses a new system.  I got gsynaptics working following the instructions here:

[https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)

I needed it to adjust the touchpad speeds were snail slow compared to the nub.

---

### Post by ChaoticMind on 2008-11-04
Worked great for me, thanks!

---

### Post by sporkubus on 2008-11-04
This is so frustrating... I have been trying to get this working properly since I first started using Ubuntu over half a year ago. My touchpad is extremely over-sensitive and I constantly lose my cursor while typing. I finally got Gsynaptics working using these instructions and turned off touchpad clicks - it worked great, at first. But it always, ALWAYS stops working at some point in the session until the next time I reboot, and touchpad clicks are turned back on. I am completely at a loss at what to do at this point. The problem has gotten irritating enough that if I can't fix it, I'm going to have to stop using Ubuntu.

---

