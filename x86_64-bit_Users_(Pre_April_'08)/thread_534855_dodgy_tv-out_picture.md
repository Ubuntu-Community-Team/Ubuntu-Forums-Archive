---
title: "dodgy tv-out picture"
date: 2007-08-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Demon1986 on 2007-08-25
finally found out how to get a picture on my tv, via my old geforce 4 card, but it seems to be missing some of the picture, and choosing different resolutions didnt work


heres how it looks on the tv:
[IMG]http://i19.tinypic.com/5xr6vrk.jpg[/IMG]

and here is on my little monitor (how it should look on the tv)
[IMG]http://i13.tinypic.com/4palshe.jpg[/IMG]

heres how the device section, of my xorg.conf file. 
> Section "Device"
	Identifier	"nVidia Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"TwinView"	"1"
	Option		"SecondMonitorHorizSync"	"30-50"
	Option		"SecondMonitorVertRefresh"	"60"
	Option		"TwinViewOrientation"	"Clone"
	Option		"TVStandard"	"PAL-B"
	Option		"TVOutFormat"	"COMPOSITE"
	Option		"MetaModes"	"1024x768 @1024x768, 800x600 @800x600, 640x480 @640x480"
	Option		"NvAGP"	"3"
	Option		"DigitalVibrance"	"0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-50
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 MX 440]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection


and i know, that the picture quality is shite, but i only got my phone to take pics with, so get used to it.

---

### Post by tjotser on 2007-08-26
I'm no expert on this but have some experience with tv's.

Option "TVStandard" "PAL-B"

Now, some TVs have a refresh of 70Hz (ntsc) and PAL 60Hz
Depending on where youi live try changing to some othe PAL mode , like PAL-N, PAL-x
Do a bit of research on  your tv's specs and you will probably find out what the TVStandard is.. 

This is all i can think of at the moment, hope something will work for you,
Are you hooked up thru S-video or Composite ? Maybe it's a defective cable ?
:( good luck

---

### Post by Demon1986 on 2007-08-26
i know so far it cant be the cable, works fine on my windows machine, the cable is a bit homemade but works. my tv is old, requires remote to adjust volume, but i can set channels myself, and i know the brand, Finlux but its a bit buggy to find the model, that old bitch is heavy :>

---

### Post by Demon1986 on 2007-09-08
long time no see.... installed a new video card yesterday, got it working today, after i found out X didnt like the change.. now the only problem so far, is my vnc viewer here, the picture on the monitor for the ubuntu comp is fine, but on the vnc viewer here the picture is messed up with the windows


[IMG]http://i9.tinypic.com/4oscitt.jpg[/IMG]


can anyone tell me how to fix that?

and also how to get the same picture as the monitor for the vnc-java thing and get tightvnc server to start automaticly, thats all i ask... for now

---

