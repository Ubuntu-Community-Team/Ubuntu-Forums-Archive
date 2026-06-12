---
title: "Dual Screen"
date: 2006-05-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by fatrabbit5 on 2006-05-08
I was wondering if it is possible to have Ubuntu run dual screens. I have ATI graphics card and was wondering if i could run a dual Screen One monitor and another Tv. I have done it with Windows XP

---

### Post by bootz52 on 2006-05-16
I agree, I am way too new at this (Linux)...i've been searching and have had trouble finding answers......can anyone also recommend some books or online/tutoral linux guides??


thanks in advance

-marc

---

### Post by FluffyElmo on 2006-05-17
Generally dual-screens and TV-out are possible, I've used both with Ubuntu. However  I'm using a Nvidia card so can't help you with specifics. Some general thoughts on where you can go from here...

1. You'll probably have to install the proprietary video driver from ATI to get full functionality. Search these forms for information on installing the driver and you should find lots of information.

2. Then check the release notes with the driver for information on enabling dual-screen or tv-out. Nvidia at least doesn't (or didn't when I installed) provide a gui for this like under Windows. You'll probably have to edit */etc/X11/xorg.conf* to set the features you need.

Good Luck, and search the forums using various phrasing. There is lots of information here but the search engine can be a little finicky in my experience.

---

### Post by bato on 2006-05-18
Hello everybody,

I have dual monitors work with ATI card. I only edited my xorg.conf file but I don't installed ati driver, I used the default driver.

Try to edit in /etc/X11/xorg.conf something like this (create a backup copy before):

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9200 Pro (RV280) 0"
	Driver		"ati"
	#BusID		"PCI:1:0:0"
	#Screen		0
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9200 Pro (RV280) 1"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"monitor0"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"screen0"
	Device		"ATI Technologies, Inc. Radeon 9200 Pro (RV280) 0"
	Monitor		"monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"ATI Technologies, Inc. Radeon 9200 Pro (RV280) 1"
	Monitor		"monitor1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Dual Head"
	Screen		0 "screen0" 0 0
	Screen		1 "screen1" RightOf "screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option	    	"Xinerama" "on"
	Option	   	"Clone" "off"
EndSection
```

If you want to try original ati drivers you have to install them before.

Good luck

---

