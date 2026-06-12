---
title: "ATI 9600 Mobility on Emachines M6805, ATI driver, video frames slow at fullscreen"
date: 2006-09-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pza3.14159 on 2006-09-23
Pardon my verbosity, I enjoy getting things (i.e. computers) to work, but I am not a computer guy by trade (at least not in a long time, and that was MacOS anyway...).:
I have an emachines M6805, 64-bit AMD 1800+, with an ATI Mobility Radeon 9600, currently running Ubuntu (Dapper) 6.06 and the AMD64 generic kernel (2.6.15-26-amd64-generic). 
I had the previous 64 bit Breezy running, with the video running apparently fine (and, amazingly enough, successfully using ndiswrapper with my apparently infamous Broadcom 43xx wireless card). 
At one point I used Synaptic to update and everything went to hell (no video).
So: I used another machine and burned an ISO of the Dapper distro you see noted above to do a fresh install of the latest and greatest. After some fits and starts I got the native wireless driver working (mostly..for some reason ndiswrapper was more problematic this time). I managed to kill the video by trying to install the ATI driver, but futzed around with the command line and eventually got it working again (not sure why, but i had the K8 kernel on the machine and it did not play well with the ATI driver..., I removed it, reinstalled the ATI driver and it worked). I then manually edited my xorg.conf using nano to add widescreen at 1280x800. So: I feel I have added most of the functionality I need, but, after enabling every repository I could think of and installing the gstreamer-0.10 packages and related libraries, I was finally able to play mpg's. However, unlike with my previous Breezy install, the video is choppy, particularly at full screen. I am not sure what this is related to, but I suspect it's something to do with the ATI driver. I've been trying to find out if the VRAM on the video card is even being used, but I'm not sure what command or file will reveal this or if I've already seen it and don't know it. I'm not sure if it's related, but I've noticed a tribble-like proliferation of xorg.conf.fglrx-0 through ...fglrx-7 files. Here is my xorg.cong, if you see anything, want to know more, or have any suggestions I'd greatly appreciate it:

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "ForceMonitors" "crtl,notv"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480" "1280x800" "1024x640"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480" "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x800" "1400x875" "1024x768" "800x600" "640x480" "1024x640"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

---

### Post by Kilz on 2006-09-23
> **Pza3.14159 said:**
> Pardon my verbosity, I enjoy getting things (i.e. computers) to work, but I am not a computer guy by trade (at least not in a long time, and that was MacOS anyway...).:
I have an emachines M6805, 64-bit AMD 1800+, with an ATI Mobility Radeon 9600, currently running Ubuntu (Dapper) 6.06 and the AMD64 generic kernel (2.6.15-26-amd64-generic). 
I had the previous 64 bit Breezy running, with the video running apparently fine (and, amazingly enough, successfully using ndiswrapper with my apparently infamous Broadcom 43xx wireless card). 
At one point I used Synaptic to update and everything went to hell (no video).
So: I used another machine and burned an ISO of the Dapper distro you see noted above to do a fresh install of the latest and greatest. After some fits and starts I got the native wireless driver working (mostly..for some reason ndiswrapper was more problematic this time). I managed to kill the video by trying to install the ATI driver, but futzed around with the command line and eventually got it working again (not sure why, but i had the K8 kernel on the machine and it did not play well with the ATI driver..., I removed it, reinstalled the ATI driver and it worked). I then manually edited my xorg.conf using nano to add widescreen at 1280x800. So: I feel I have added most of the functionality I need, but, after enabling every repository I could think of and installing the gstreamer-0.10 packages and related libraries, I was finally able to play mpg's. However, unlike with my previous Breezy install, the video is choppy, particularly at full screen. I am not sure what this is related to, but I suspect it's something to do with the ATI driver. I've been trying to find out if the VRAM on the video card is even being used, but I'm not sure what command or file will reveal this or if I've already seen it and don't know it. I'm not sure if it's related, but I've noticed a tribble-like proliferation of xorg.conf.fglrx-0 through ...fglrx-7 files. Here is my xorg.cong, if you see anything, want to know more, or have any suggestions I'd greatly appreciate it:

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "ForceMonitors" "crtl,notv"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480" "1280x800" "1024x640"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480" "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x800" "1400x875" "1024x768" "800x600" "640x480" "1024x640"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


Are you running the driver in the repositories, or one from ati? If its from ati, what version?

---

### Post by Pza3.14159 on 2006-09-23
From ATI:
ATI Proprietary Linux x86_64 Display Driver for XFree86 / X.Org Version 8.28.8

---

### Post by Kilz on 2006-09-23
> **Pza3.14159 said:**
> From ATI:
ATI Proprietary Linux x86_64 Display Driver for XFree86 / X.Org Version 8.28.8

8.28.8 isnt the greatest at acceleration. Im using 8.26.18 for that reason.

---

### Post by Pza3.14159 on 2006-09-23
Thanks for the tip, I might try it after backing up my documents. Do you think I can just install the new (old) driver, or should I uninstall/delete things first?
thanks, bruce

---

### Post by Kilz on 2006-09-23
> **Pza3.14159 said:**
> Thanks for the tip, I might try it after backing up my documents. Do you think I can just install the new (old) driver, or should I uninstall/delete things first?
thanks, bruce

I just used the gpkg -i --force-overwrite *.deb last time I did it to install the deb's the installer makes. Worse comes to worse all that happens is you ```
dpkg-reconfigure xserver-xorg
``` and use the ati drivers to start ubuntu then reinstall the 8.28.8 drivers.

---

