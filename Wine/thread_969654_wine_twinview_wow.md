---
title: "wine twinview wow"
date: 2008-11-03
forum: Wine
---

### Post by jinxi on 2008-11-03
hiho
I'm really lost at the moment! hope you can help me.
I run Ubuntu since 7.10 still the same hardware.

Hardware:
Nvidia 8800gtx
asus striker board
2 Screens (Twinview) 17"

Software:
wine
wow

7.10 run perfect. just restricted and nvidia-settings.
I could watch tv on one screen, and play wow on the other... no problem

8.04 couldn't run 2 grafic tools on same time :(

now 8.10 even wow doesn't run anymore
I'm at the point to install 7.10 again ;)

Problem:
I want to ran my station with twinview, I start wow with -opengl (like ever) the wine window shrinks to somthing streng. seems like he take the settings of to screen (2480x1024) and puts it into one screen :S
Ignoring that, I try to loggin. I recognize that the graphiccard makes more noice then normally. pflupp the computer shuts down. I tried it with separate screen, with both restricetet drivers and so on.

I will post you my xorg.conf because probably there is somthing wrong.

thanks for help!

---

### Post by jinxi on 2008-11-03
Section "Monitor"
	Identifier     "Configured Monitor"
EndSection

Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "SAMSUNG"
	HorizSync       30.0 - 81.0
	VertRefresh     56.0 - 75.0
EndSection

Section "Screen"
	Identifier     "Default Screen"
	Device         "Configured Video Device"
	Monitor        "Configured Monitor"
	Option         "NoLogo" "True"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
		Modes      "nvidia-auto-select"
	EndSubSection
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	Option         "TwinView" "1"
	Option         "TwinViewXineramaInfoOrder" "CRT-1"
	Option         "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: nvidia-auto-select +1280+0"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "Module"
	Load           "glx"
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "keyboard"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
	Identifier     "Configured Video Device"
	Driver	"nvidia"
EndSection

Section "Device"
	Identifier     "Device0"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce 8800 GTX"
	Option	"NoLogo"	"True"
	Driver	"nvidia"
EndSection

Section "ServerFlags"
	Option         "Xinerama" "0"
EndSection

---

### Post by jinxi on 2008-11-03
can nobody help me? is someone with similar problems here?

---

### Post by jinxi on 2008-11-19
nobody can help me? why are these crushes? what part of my f.. system is wrong? driver (sound, graka) wine wow ?

---

