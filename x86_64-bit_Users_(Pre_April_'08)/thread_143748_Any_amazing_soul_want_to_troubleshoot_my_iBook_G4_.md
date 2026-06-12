---
title: "Any amazing soul want to troubleshoot my iBook G4 compiz/xgl situation? pleeeease"
date: 2006-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by spaceballl on 2006-03-13
To anyone who knows this well, thanks for the help!

These are the steps I followed:

1. Install all of the packages.

2. Modfiy my /etc/gdm/gdm.conf to look as follows:
Under servers..
```

[servers]
# 0=Standard
1=Xgl

```

3. Modified my /etc/gdm/gdm.conf-custom to look like this:
```

[servers] 
1=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true

```

4. For kicks, here's my xorg.conf
```

Section "Device"
	Identifier	"ATI Technologies, Inc. M9+ 5C63 [Radeon Mobility 9000 (AGP)]"
	Driver		"radeon"
	BusID		"PCI:0:16:0"
	Option	"AGPMode" "4"
	Option	"AGPFastWrite" "yes"
	Option	"EnablePageFlip" "on"
	Option	"ColorTiling"	"on"
	Option	"RenderAccel" "yes"
	#Option	"UseFBDev" "true" DISABLED!
	Option "EnableDepthMoves" "true"
	Option "BackingStore" "true"
	Option	"DynamicClocks"	"on"
EndSection

Section "Extensions"
    Option "Composite" "true"
EndSection

```
I know it is properly accelerating things because I get between 30 and 60 fps in tuxracer, before I changed this file I was using the "ati" driver and I was getting between 10 and 27 fps.

5. So at this point, I think i'm ready to go. Reboot the system. Everything is normal. I get into gnome, and things seem a bit sluggish, but they work. I run the following script:
```

#!/bin/bash
xmodmap /usr/share/xmodmap/xmodmap.us # I live in the U.S.
gnome-window-decorator &
compiz --replace gconf &

```

At this point, I have no more window manager, things are behaving oddly, the system is incredibly slow. A few scattered graphical errors, and that's it.

If anyone has some suggestions, I would love them!!!

---

### Post by ssam on 2006-03-13
could you try adding export DISPLAY=:1 to that script

```

#!/bin/bash
**export DISPLAY=:1**
xmodmap /usr/share/xmodmap/xmodmap.us # I live in the U.S.
gnome-window-decorator &
compiz --replace gconf &
```

then instead of running from a terminal in gnome:
press CRTL+ALT+F1
log in
run the script.

this way you should get a useful error message.

---

### Post by spaceballl on 2006-03-13
Hey SSAM,

Thanks for the response. I tried your method, but now once I get to the prompt, when i run the script, it just hangs... The cursor moves onto the next line and flickers infinitely. You're running on an iBook G4 too right? Did you follow similar steps to set it up?

-Kevin

---

