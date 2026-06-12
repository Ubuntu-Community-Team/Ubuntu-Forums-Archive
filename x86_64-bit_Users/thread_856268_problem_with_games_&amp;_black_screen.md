---
title: "problem with games &amp; black screen"
date: 2008-07-11
forum: x86 64-bit Users
---

### Post by DariusS on 2008-07-11
Ok, I've done a plethora of research on this one and can't find a fix. Every time I try to load up a game, all I get is a black screen after the resolution appears to change. The only game I can run without this happening so far is Urban Terror. I'm currently trying to get Wolfenstein: Enemy Territory working, but alas to no avail. Other archive threads I've found allude to it being an issue with xorg.conf, but I can't figure out what exactly as all these posts were for older versions (hoary and warty I believe).
I'm currently running Hardy 64bit with an nvidia geforce 6800gt. all latest drivers intstalled, etc. and yes, I've tried disabling compiz before starting the game. I know OpenGL is working.
The only odd thing I've found, and it probably is irrelevant, is that the nvidia settings app shows my res at 1600x1200 ref. @ 75hrtz while in system>preferences>screen resolution it shows a ref. of 50hrtz.

any help or suggestions will be greatly appreciated.

---

### Post by Artemis3 on 2008-07-12
I have always seen the hz reported by that gnome app screwed like that, usually the lower value is the highest.

My current resolution is 1792x1344, monitor reports 75hz, nvidia tool reports 75hz, screen resolution shows 50hz. Setting it to "60hz" only slows it down.  It was like that with 7.10, 7.04 iirc.

1024x768, for example in the screen resolution (gnome) thing, offers: 84hz, 83hz, 81hz, 80hz, and 54hz. I know from experience, to have the highest refresh, choose "54hz". This in reality means (for this monitor) 100hz. The other values would slow it a little bit, with "80hz" being 85hz, "81hz" 75hz, "82hz" 72hz, "83hz" 70hz, and "84hz" 60hz.

So rule of thumb, when fiddling with "screen resolution", just pick the "slowest" weird number you see first :)

For your video issues, test if games like openarena or tremulous work fine. Sometimes ET config becomes weird, so delete .etwolf folder (rm -r ~/.etwolf). Run the game from the console to see if you get some error.

---

### Post by soxs on 2008-07-12
plx post the output from ```
cat /etc/X11/xorg.conf
``` (this will show your whole xorg.conf in a console window)

---

### Post by DariusS on 2008-07-12
Here's my xorg.conf, minus all the commented out lines:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	Option		"TwinView"	"0"
	Option		"TwinViewXineramaInfoOrder"	"CRT-0"
	Option		"metamodes"	"1600x1200_75 +0+0"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Device"
	Identifier	"Videocard0"
	Driver		"nvidia"
	Vendorname	"NVIDIA Corporation"
	Boardname	"GeForce 6800 GT"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Screen0" 0 0
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Unknown"
	Modelname	"Daewoo Insignia"
	Horizsync	30.0	-	95.0
	Vertrefresh	50.0	-	160.0
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"0"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

---

### Post by soxs on 2008-07-13
Do you have 2 monitors and gpus??? at least this is what your xorg.conf says, though it lacks some upspeeding options.
Plx answer, I will then adjust your xorg.conf tzo our needs and/or guide you through

---

### Post by DariusS on 2008-07-13
No, 1 gpu, a geforce 6800gt. only one monitor.

---

### Post by soxs on 2008-07-13
```
Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
#	Option		"TwinView"	"0"
#	Option		"TwinViewXineramaInfoOrder"	"CRT-0"
#	Option		"metamodes"	"1600x1200_75 +0+0"

	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Videocard0"
	Driver		"nvidia"
	Vendorname	"NVIDIA Corporation"
	Boardname	"GeForce 6800 GT"

	Option		"AllowGLXWithComposite"		"1"
	Option          "RenderAccel"           "1"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Screen0" 0 0
EndSection

Section "Module"
        Load    "glx"
        Load    "dbe"
        Load    "v4l"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Unknown"
	Modelname	"Daewoo Insignia"
	Horizsync	30.0	-	95.0
	Vertrefresh	50.0	-	160.0
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"0"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option	"Composite"	"1"
	Option	"RENDER"	"1"
        Option	"DAMAGE"	"1"
EndSection
```

give this a try, but keep your old one as backup, so you can easily revert if something goes wrong.

---

### Post by DariusS on 2008-07-14
Good news: the xorg.conf you gave me didn't break my system.
Bad news: nor did it solve my problem with ET :(

also, slightly unrelated question, whats the difference between using sudo/gksudo and su/gksu?


anyway, thanks for the help!

---

### Post by soxs on 2008-07-14
Deleted..  wasn't usefull at all

---

### Post by soxs on 2008-07-14
one is graphical one is terminal only.

Plx post the autput from:
```
glxinfo|grep render
```

---

