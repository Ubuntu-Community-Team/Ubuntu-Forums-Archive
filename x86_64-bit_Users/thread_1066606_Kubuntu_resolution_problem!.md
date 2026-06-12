---
title: "Kubuntu resolution problem!"
date: 2009-02-11
forum: x86 64-bit Users
---

### Post by Racle on 2009-02-11
i installed kubuntu 3 days ago, and still can't figure why i cant set my resolution to 1680x1050! i tryd conf xorg.org, but that didnt work, i tryed radeonhd, that didn't work eather. now i got ati own drivers installed, but even i use 
aticonfig --resolution=0,1680x1050 command, and that makes new xorg.conf, i cant still get to that resolutin. higest is 1600x1200, what is too big,  and what i use now, is 1400x1050, what si way too low.

my xorg.conf [http://pastebin.com/f40b14f83](http://pastebin.com/f40b14f83)
i have tryed diffrent variations of that file, but nothing seems to work :/

And i have 60bit kubuntu 8.10 and ati radeon HD4850

---

### Post by marttali on 2009-02-11
Have you tried to change your resolution from kubuntu's "configure your desktop" and display from there ?

---

### Post by samuelosss on 2009-02-11
Hi there

Got the same problem, installed ATI drivers, xorg.conf looks like this: 
[INDENT]Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes "1680x1050"
	EndSubSection
EndSection[/INDENT]]

And still in xrandr there are options only "1600x1200" or "1440x900"

And I am sure I got the proper driver, it recognizes my card:
[INDENT]~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4350
OpenGL version string: 2.1.8395 Release[/INDENT]

How can I get "1680x1050" ??? Is there a way to fool xrandr to use res. not defined by it?

Many thanks

---

### Post by Racle on 2009-02-11
> **marttali said:**
> Have you tried to change your resolution from kubuntu's "configure your desktop" and display from there ?

Can't see anything from that list, so i mean 1650x1050 resolution, higest is 1600x1200 but that way to  high

---

### Post by samuelosss on 2009-02-12
Hey Racle

After lots of hours spent on forums round the net, I came to solution which works for me:

I put this line:
```
Modeline 	"1680x1050" 149.00  1680 1760 1944 2280  1050 1050 1052 1089
```

in section "Monitor" of xorg.conf

Your values maybe different, check this [http://www.bohne-lang.de/spec/linux/modeline/](http://www.bohne-lang.de/spec/linux/modeline/)  to get the right values for you monitor..
Write if it worked for you

I still have to play with lots of stuff, to get everything running mint, but at least resolution is now set on max. for my monitor (Acer V223W).

---

