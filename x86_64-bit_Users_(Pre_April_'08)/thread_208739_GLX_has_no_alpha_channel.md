---
title: "GLX has no alpha channel?"
date: 2006-07-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kazade on 2006-07-04
Hi everyone,

I'm having some really annoying problems getting my OpenGL applications to work. For some reason, everytime I try any OpenGL program that requires 32bit color (24+alpha) GLX complains that it can't find a matching visual. I have reinstalled Dapper 3 times, and installed both the included ATI drivers, and the proprietry ones, and its always the same thing. I can't run any OpenGL programs because of this. 

Here is the output from glxinfo:

> 
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  1 0 None
0x2b 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x2c 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x2d 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x2e 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x2f 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x34 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x35 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x36 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x37 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x3c 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x3d 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x3e 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x3f 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  6 1 None
0x43 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x44 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x45 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x46 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x47 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x48 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x49 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  1 0 None
0x4a 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  1 0 None
0x4b 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x4c 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x4d 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x4e 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x4f 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  2 1 None
0x50 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  2 1 None
0x51 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  2 1 None
0x52 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  2 1 None
0x53 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x54 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x55 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x56 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x57 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  4 1 None
0x58 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  4 1 None
0x59 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  4 1 None
0x5a 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  4 1 None
0x5b 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x5c 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x5d 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x5e 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x5f 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  6 1 None
0x60 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  6 1 None
0x61 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  6 1 None
0x62 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  6 1 None


Notice that the alpha channel in the colour buffer is always 0. glxgears does work, but I assume that this doesnt try to allocate space for an alpha channel. I'm running 64bit Kubuntu, and I know that this is probably a 64 bit problem. DRI rendering is enabled.

Just in case it helps, here's my xorg.conf:

> 
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	#Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	DefaultFbBpp 	 32
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
	SubSection "Display"
		Viewport 	0 0
		Depth	16
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


Can anyone help me, I think im gonna cry if I dont get this working soon! :)

Luke.

P.S. I have an ATI Radeon 9550

---

### Post by Kilz on 2006-07-04
[QUOTE=Kazade]Hi everyone,

I'm having some really annoying problems getting my OpenGL applications to work. For some reason, everytime I try any OpenGL program that requires 32bit color (24+alpha) GLX complains that it can't find a matching visual. I have reinstalled Dapper 3 times, and installed both the included ATI drivers, and the proprietry ones, and its always the same thing. I can't run any OpenGL programs because of this. 

Here is the output from glxinfo:



Notice that the alpha channel in the colour buffer is always 0. glxgears does work, but I assume that this doesnt try to allocate space for an alpha channel. I'm running 64bit Kubuntu, and I know that this is probably a 64 bit problem. DRI rendering is enabled.

Just in case it helps, here's my xorg.conf:



Can anyone help me, I think im gonna cry if I dont get this working soon! :)

Luke.

P.S. I have an ATI Radeon 9550[/QUOTE]

The 8.25.18 drivers were awful, I have read a few people alread complain about the 8.26.18 drivers that were just released. I had to wipe down to get rid of the 8.25.18 so I dont trust the new ones. I installed the 8.24.8 drivers and locked them into place in synaptic. I wont upgrade them untill Edgy, maybe by then things will work. In case you would liek to try them I do know the 8.24.8 drivers are avaiable from ATI but I had to copy link location, paste it in the address bar, and edit the driver version number.
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.24.8-x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.24.8-x86_64.run)

---

### Post by Kazade on 2006-07-04
Is this a known bug with those drivers then? I'll give it a go tonight. It's strange I have searched all over the internet for people with the same problem, but ive found nothing. Yet this problem continues after several installs of Dapper, surely other people must have this problem?

Luke.

---

### Post by Kilz on 2006-07-04
[QUOTE=Kazade]Is this a known bug with those drivers then? I'll give it a go tonight. It's strange I have searched all over the internet for people with the same problem, but ive found nothing. Yet this problem continues after several installs of Dapper, surely other people must have this problem?

Luke.[/QUOTE]
I don't think your particular problem is known, but those drivers are sad sad sad. So its possible they are at fault. After installing 3 times, its an even bigger possibility imho. But I'm not a expert, just offering options.

---

### Post by Kazade on 2006-07-05
I tried to install the 8.24 drivers, but I couldnt because of missing dependencies, so I reinstalled the 8.25 ones and the same error occurred. Then I read that I should remove the file, /etc/X11/Xsession.d/10fglrx, if it exists. Which I did. Now, glxinfo cant find fglrx_dri.so, and if I export the path, then run it I get the same output as before, so now i've done more damage. 

Anyone have any suggestions? 

I'm still at a loss as to why I have so few video modes available.

Luke.

---

### Post by Kilz on 2006-07-05
[QUOTE=Kazade]I tried to install the 8.24 drivers, but I couldnt because of missing dependencies, so I reinstalled the 8.25 ones and the same error occurred. Then I read that I should remove the file, /etc/X11/Xsession.d/10fglrx, if it exists. Which I did. Now, glxinfo cant find fglrx_dri.so, and if I export the path, then run it I get the same output as before, so now i've done more damage. 

Anyone have any suggestions? 

I'm still at a loss as to why I have so few video modes available.

Luke.[/QUOTE]
Missing dependencies? I didnt run into that, what was missing?

---

### Post by ViX666 on 2006-07-06
[QUOTE=Kilz]The 8.25.18 drivers were awful, I have read a few people alread complain about the 8.26.18 drivers that were just released. I had to wipe down to get rid of the 8.25.18 so I dont trust the new ones. I installed the 8.24.8 drivers and locked them into place in synaptic. I wont upgrade them untill Edgy, maybe by then things will work. In case you would liek to try them I do know the 8.24.8 drivers are avaiable from ATI but I had to copy link location, paste it in the address bar, and edit the driver version number.
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.24.8-x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.24.8-x86_64.run)[/QUOTE]

I have been having issues with 8.26.18 as well. I'll try installing them again on a fresh Ubuntu install and report the progress here. If bad comes to worse, I will first try to install 8.24.8 and if that doesn't work either, install Ubuntu 32 bit *shudder*. And I just wanted to discover the wonders of Compiz myself.. *sob*

Qwik Spex - HP DV5120US Notebook with AMD Turion® 64 ML and ATI Radeon Xpress 200M

---

### Post by Kilz on 2006-07-06
[QUOTE=ViX666]I have been having issues with 8.26.18 as well. I'll try installing them again on a fresh Ubuntu install and report the progress here. If bad comes to worse, I will first try to install 8.24.8 and if that doesn't work either, install Ubuntu 32 bit *shudder*. And I just wanted to discover the wonders of Compiz myself.. *sob*

Qwik Spex - HP DV5120US Notebook with AMD Turion® 64 ML and ATI Radeon Xpress 200M[/QUOTE]
What issues did you have with the 8.26.18 drivers?

---

### Post by Kazade on 2006-07-06
Ok, I'm not sure this is a problem with the drivers, I only have a few video modes no matter what version I have installed. OpenGL works correctly (if I edit my own openGL programs to run in one of the few modes I have) and hardware accelerated. I need to know where the modes from glxinfo are read from, and more specifically what software (drivers?, xorg?) reads them on bootup?

---

