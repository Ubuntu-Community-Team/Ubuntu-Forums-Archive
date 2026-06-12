---
title: "ATI card problem..."
date: 2005-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by teme82 on 2005-10-30
Hi!
I have a X800 GTO PCI-E gfx card and I was just wondering is there drivers that has support for this card? It has R480 core, I've opened it and checked it.
And for some reasons forum don't allow mee to put Xorg.0.log to here so I packed it :D

---

### Post by gfx on 2005-10-30
Yes it picks the wrong driver...
Try using the radeon driver instead of ati
in the file /etc/X11/xorg.conf

After editing it will look something like this:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X800 XL (R430 UM)"
	Driver		"radeon"
	BusID		"PCI:5:0:0"
EndSection

---

