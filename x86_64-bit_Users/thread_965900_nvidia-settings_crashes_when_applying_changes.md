---
title: "nvidia-settings crashes when applying changes"
date: 2008-10-31
forum: x86 64-bit Users
---

### Post by maxxum on 2008-10-31
I have a dual screen setup with a Nvidia Quadro FX570 card. I have been using this setup in 8.04 (x64) without problems. Now in 8.10 64-bit, the nvidia-settings crashes and on the terminal where I started it from, I see Segmentation fault. 
I will revert to 8.04 until I find a solution to this issue but if anyone can suggest any corrective measures...I will be grateful!

The driver however, is working. I have compiz and visual effects working. Here is the complete xorg.conf:
```
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

```
EDIT: I have been able to get twinview to work since it does not require X-server restart. But the settings are not being saved to the X-configuration file because it crashes as soon as I click on the save button.

---

### Post by Akita on 2008-11-01
Here too on a 8600GT. Driver is fine, manual changes to the file are fine. Can't save any changes made with nvidia-settings without the app crashing.

---

### Post by GriZzm0 on 2008-11-01
I noticed the same thing. You need to run nvidia-settings as root to be able to save the changes otherwise it crashes.

---

### Post by xandones on 2008-11-01
The system frequently crashes when I install a new package. I have to use the recovery mode and it always disables the Nvidia video board.

---

### Post by evilkastel on 2008-11-01
It's a bug. Check my post "Found Nvidia driver Ibex Solution" (Google it ;)) there is explained and described a workaround.

---

### Post by avangardman on 2008-11-01
Try to install linux-headers to sinchronize kernel and nvidia driver

---

### Post by maxxum on 2008-11-02
evilkastel,
Thanks! your workaround worked fine!

---

