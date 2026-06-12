---
title: "Sometimes I get small titlebars"
date: 2008-03-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by whoop on 2008-03-06
Sometimes when I boot ubuntu and get into gnome my title bars are about half the height they should be. They also have small text on them...
I am running compiz. The way I work around this is changing the visual effects to none and then back to custom again... But off course it should not be happening at all.

Any ideas?

---

### Post by nutz on 2008-03-06
try adding the lines in bold to your xorg.conf...


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
	Option  "DPMS"  "true"
**        Option "UseEdidDpi" "FALSE"**
**        Option "DPI" "100x100"**
EndSection

Set the DPI to whatever looks good to you. I think 96x96 is default....

---

