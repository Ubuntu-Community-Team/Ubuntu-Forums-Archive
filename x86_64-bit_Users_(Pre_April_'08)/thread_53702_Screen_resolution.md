---
title: "Screen resolution"
date: 2005-08-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by NikoO on 2005-08-01
Hello there,

Well, I've a problem with my screen resolution, I can't get more than 1024*768, I installed ATI Drivers, but it doesn't change anything!

Here is my xorg.conf

> 

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X800 Pro (R420 JI)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Écran génériquePana1ssss"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X800 Pro (R420 JI)"
	Monitor		"Écran génériquePana1ssss"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

 

If someone could help me, it would be very cool :)

Thanks guys,
Nicolas

---

### Post by jss on 2005-08-01
NikoO, 
I had the same problem. Corrected it by setting HorizSync and vertical refresh to manufacturer's specs ( obtained on their website ). In my case it was 30 - 81 horizontal and 56 -75 vertical though it is important to follow manufacture's recommendation.  I also added screen resolution I wanted to xorg.conf. hope this helps.

---

### Post by negatory on 2005-08-02
You must add  the resolution you want to the Modes line.
Like this:```
 Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
```
Then restart your X server with "ctrl + alt + backspace"
That's all.
Pedro Carrico

---

### Post by heimo on 2005-08-02
Couple links which may be helpful:

[https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)
[http://www.ubuntuforums.org/showpost.php?p=105064&postcount=1](http://www.ubuntuforums.org/showpost.php?p=105064&postcount=1)
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

