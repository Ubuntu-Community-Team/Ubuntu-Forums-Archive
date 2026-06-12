---
title: "Geforce 8300 integrated problem(no, not hdmi)"
date: 2009-05-30
forum: x86 64-bit Users
---

### Post by krazydbiker on 2009-05-30
Hey guys, for the life of me I can not get the nvidia drivers to install right. I've tried envy, and through ubuntu. (using 9.04x64 btw). 
The drivers install alright, and everything works, except when I try to view glxgears I get :

Xlib:  extention "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

And this is my xorg.conf. For some reason it looks a little small:

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




It's outputting through hdmi to 1080p, if you need that information.
any ideas? I've tried the latest 180 drivers and the previous 173, both with the same result.

---

