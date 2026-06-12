---
title: "The wonderful world of ATI......."
date: 2006-02-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Blairboy on 2006-02-18
So here's the skinny.  I used the official ati driver installation guide (amongst others before), and every time i do so, x won't load.  The error I get from X is this:

(WW) RADEON: No matching Device section for instance (BusID:5:0:1) found.

which is rather confusing because my xorg.conf reads as such:

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "ati"
	Option	    "UseFBDev" "true"
	BusID       "PCI:5:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	BusID       "PCI:5:0:0"
EndSection



I found it rather odd that xorg.conf specifies 5:0:0, but X is bitching about 5:0:1.  Any ideas on how to get this crapola to actually work?

PS-I'm using an ATI x1600xt video card, AMD 4200+ X2, 4GB of ddr400 ram, running the 64 bit version of ubuntu.

---

### Post by newuser111 on 2006-02-18
you can't have 2 device sections in the xorg.conf, there should only be one driver

run sudo dpkg-reconfigure xserver-xorg and select fglrx

btw im not sure if your card is supported by the fglrx drivers read around on this forum [http://www.rage3d.com/board/forumdisplay.php?f=92](http://www.rage3d.com/board/forumdisplay.php?f=92)

---

### Post by Blairboy on 2006-02-18
"Sorry to disappoint you, but the X1k series are unsupported as of yet (fglrx
and radeon).
For the time being, you have to use the vesa driver."

Hooray.  So there's no support from the actual ATI driver?

---

