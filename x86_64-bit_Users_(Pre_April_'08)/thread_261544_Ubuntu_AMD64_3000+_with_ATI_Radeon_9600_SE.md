---
title: "Ubuntu AMD64 3000+ with ATI Radeon 9600 SE"
date: 2006-09-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bunro on 2006-09-20
Problem with: Ubuntu AMD64 3000+ with ATI Radeon 9600 SE

I installed Ubuntu AMD64 version 6.06 with the latest updates installed.
The problem is that I can not get in to the graphical site of the system.
I have read for may days now different forums about ATI problems but until now I cant get the system running normally. 

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide/](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide/)

After the installation fase I made the following checks:
fglrxinfo
Error: unable to open display :0
-----------------------------------------------------------
sudo pico /etc/X11/xorg.conf
gives at the end:
Section “Device”
	Indentifier 	“ATI Technologies, Inc. RV350 AQ [Radeon 9600 SE]”
	Driver		“fglrx”
	BusID		“PCI:1:0:0”
	VideoRam	128
	Option		“UseFBDev”	“true”
EndSection
--------------------------------------------------------------
pico /var/log/Xorg.0.log
Gives the following:
(WW) RADEON: No matching “Device” section “ATI Technologies, Inc. RV350 AQ [Radeon 9600 SE]”.
(II)Module fbdevhw: vendor=”X.Org Fondation”
compiled for 7.0.0, module version = 0.0.2
ABI class: X.Org Video Driver, version 0.8
     (WW) open /dev/fb1: No such file or directory
     (WW) open /dev/fb2: No such file or directory
     (WW) open /dev/fb3: No such file or directory
     (WW) open /dev/fb4: No such file or directory
     (WW) open /dev/fb5: No such file or directory
     (WW) open /dev/fb6: No such file or directory
     (WW) open /dev/fb7: No such file or directory
     (EE) RADEON(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
	(you may have to look at the server log to see warnings)
     (WW) RADEON (0): fbdevHWInit failed, not using framebuffer device
...
...
...
  (EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open DRM
[dri] Disabling DRI.
...
...
...
(WW) RADEON (0): Failed to detect secondary monitor, mergeDFB/Clone mode disabled

At the end
xf86MapVidMem: Could not mmap framebuffer (0xd0000000,0x0) (Invalid argument)
---------------------------------

Hopefully there is someone that can help me out!

Regards, Robert

---

### Post by the_burk on 2006-11-14
Section “Device”
Indentifier “ATI Technologies, Inc. RV350 AQ [Radeon 9600 SE]”
Driver “fglrx”
BusID “PCI:1:0:0”
VideoRam 128
Option “UseFBDev” “true”
EndSection


try changing to Option "UseFBDev" "false"

---

