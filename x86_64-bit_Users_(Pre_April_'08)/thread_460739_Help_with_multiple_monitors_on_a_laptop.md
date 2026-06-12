---
title: "Help with multiple monitors on a laptop"
date: 2007-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Deathwish238 on 2007-06-01
What do I need to do to get Ubuntu to automatically set the external monitor as the primary monitor whenever it is connected?  I suppose I first need to worry about enabling it the external monitor...any help with how to do so would be appreciated.  I don't care for the laptop top's monitor and external monitor to be separate of each other, I would prefer if they were just clones.

---

### Post by TeKniKal on 2007-06-01
What kind of graphic card have you got.

If you have an nVidia for instance, I would recommend to  get the binary drivers to work (which can be a pain in the ***, but many good guides exist), then you get a Windows-like interface to adjust your settings, including setting up different monitors, which lets you do some things quite on-the-fly, but for others you will need to edit the xorg.conf file (requires root privileges, but can be done from within the nvidia control panel (if it is launched with root privileges by running "gksudo nvidia-settings", so it will require you to restart the X server).

Personally I have the current setup: a notebook with an nVidia card, which clones my output (different X screens, so not quite the nVidia twinView way) onto two monitors (which have the same native resolution, but different native resolutions should work too I guess (as long as you work on the highest common this is certainly possible, I don't know if the linux drivers can do something similar to Windows (if you pick a larger resolution that it will pan the high res screen image on the low-res screen).

---

### Post by Deathwish238 on 2007-06-05
Unfortunately I don't have an Nvidia card, I have an ATI Radeon x700 Mobility

Do you know if such a thing exists for ATI cards?

---

### Post by dmfield on 2007-06-05
As a dell inspiron 1501  with an ATI card, i'd also like to know how to do this, i'vce got the ATI.com drivers loaded. I tried it on Kubuntu but the mouse cursor on the external Dell 17" display was a square, not a cursor. Now i'm running 7.04

---

### Post by Deathwish238 on 2007-06-06
Are the drivers that load by default not the ATI drivers?

---

