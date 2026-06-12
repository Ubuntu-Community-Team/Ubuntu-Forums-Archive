---
title: "Ati Tv-out"
date: 2006-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by kurushi on 2006-01-05
Hi

I installed the ATI propietary drivers and they are working properly with 3D acceleration, but I can't make work the TV-OUT.  I've an X600 PCI Express card and I'm using Breezy for 64 bits, this is my xorg.conf (section) file :

	Option "DesktopSetup"               "Clone"
	Option		"MonitorLayout"	"STV, AUTO"

	Option "NoTV"                       "no"
	Option "TVStandard"                 "PAL-G"
	Option "TVHSizeAdj"                 "0"
	Option "TVVSizeAdj"                 "0"
	Option "TVHPosAdj"                  "0"
	Option "TVVPosAdj"                  "0"
	Option "TVHStartAdj"                "0"
	Option "TVColorAdj"                 "0"
	Option "GammaCorrectionI"           "0x06419064"
	Option "GammaCorrectionII"          "0x00000000"

I don't know how to set up, I googled for information about the other driver (Driver "ati"), but looks like there's not information with the TV-OUT option. 

If somebody can give me help I'll agree, thanks in advance

Albert

---

### Post by Chris Tucker on 2006-01-05
(not amd64 but...) im having a problem with my radeon 7000 too... tv out is always in clone mode, no matter the xorg settings, and when using driver "vesa" all works well (except performance is horrible and so is 3D.) both attempts with driver "ati" and "radeon" have managed to make the tv output what seems to be out of sync.. despite using 60hz and 800x600 , which worked with vesa... the picture is quite odd... 
[[IMG]http://img263.imageshack.us/img263/4232/pict00011ey.jpg[/IMG]](http://imageshack.us)
above is the ubuntu login screen when using driver "radeon" .. same appears for "ati"

---

