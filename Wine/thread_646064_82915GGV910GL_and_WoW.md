---
title: "82915G/GV/910GL and WoW"
date: 2007-12-20
forum: Wine
---

### Post by tj111 on 2007-12-20
My little brother was having alot of issues with his PC, so being a good big brother I helped him uninstall windows and install Ubuntu,  It work's great on his computer, hasn't had any issues, but he wants to play WoW on it.  WoW ran great under XP on his computer, but now it runs at like 0.5fps.  

I'm pretty sure it has to do with his video card/drivers.  He has a Intel 2915G/GV/910GL Integrated Graphics Controller, but under device manager it says "Device Type: Unknown, Capabilites: Unkown".  So I went to his xorg.conf, and here's what he has regarding his video card:
> 
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"DELL E196FP"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"DELL E196FP"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection


I think it should have his 82915G/GV/910GL listed as the Device with some Intel drivers, instead of just "Generic Video Card".  I've done some searching, but can't seem to find any Intel/Linux drivers.  Anyone have any recommendations?

---

### Post by The Noble on 2007-12-20
Yes, the laptop is lacking the drivers to run, so you don't have any 3d acceleration. From a brief jaunt around the web, I found that your card uses the i810 driver. I believe Ubuntu already has this driver installed. Therefore, if you are even remotely comfortable with the command line (this may not work perfectly...), you should replace
```

Driver "vesa"

```
with
```

Driver "i810"

```
 This will use the driver for your card, which should have been used from the start (I guess ubuntu did not get the autodetection right...). Be careful though, and have a livecd ready. If this fails, you will be dropped into the command line after you restart X. If that happens to you, use 
```

sudo nano /etc/X11/xorg.conf

```
and revert to your previous vesa driver. Good luck.

---

### Post by tj111 on 2007-12-21
Thanks alot.  I will give this a shot tomorrow.

---

### Post by tj111 on 2007-12-22
Thanks, this worked great.  Chenged the driver, restarted the x server, and everything works.  I even put compiz fusion on there now.

---

### Post by The Noble on 2007-12-23
Hey sounds good. I hope you don't have any more problems with WoW.

---

