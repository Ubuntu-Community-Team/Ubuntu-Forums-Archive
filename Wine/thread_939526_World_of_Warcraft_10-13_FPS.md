---
title: "World of Warcraft 10-13 FPS"
date: 2008-10-06
forum: Wine
---

### Post by Omeil on 2008-10-06
Hi im running Ubuntu 8.04 LTS, I have WINE 1.1.5 installed and when i play world of warcraft i get between 7-12 FPS in Orgrimmar somtimes it might even freeze for 1-2 seconds:

FGLRXINFO:

 ```
oliver@oliver-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2600 Pro AGP
OpenGL version string: 2.1.7979 Release

```

glxgears:

```

oliver@oliver-desktop:~$ glxgears
6312 frames in 5.0 seconds = 1262.276 FPS
7153 frames in 5.0 seconds = 1430.556 FPS
5406 frames in 5.0 seconds = 1081.189 FPS
7071 frames in 5.0 seconds = 1414.035 FPS
7591 frames in 5.0 seconds = 1518.119 FPS
6785 frames in 5.0 seconds = 1356.842 FPS
7613 frames in 5.0 seconds = 1522.559 FPS
7613 frames in 5.0 seconds = 1522.456 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 64 requests (64 known processed) with 0 events remaining.
oliver@oliver-desktop:~$ 

```

Xorg.conf:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option      "Capabilities" "0x00000800"
	Option	    "UseFastTLS" "off"
	Option      "KernelModuleParm" "locked-userpages=0" 	
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

In windows i used to get 33+ FPS outside, also my map on top right corner is white. if anyone could help it would be great, I have amended config.wtf with the configs from the tutorials and alos the disable extention buffer.

---

### Post by alynx on 2008-10-06
Hope this topic will help 

[http://ubuntuforums.org/showthread.php?t=579378&highlight=wow+wine](http://ubuntuforums.org/showthread.php?t=579378&highlight=wow+wine)

I got wow to run ok with this with an older wine app so hopefully this is better now

---

### Post by Omeil on 2008-10-06
Hi thanks for the reply, I tried running WoW under its own X server using,

#!/bin/sh
 
X :3 -ac &   # Launches a new X session on display 3 
cd /home/oliver/games/wow/
sleep 2   # Forces the system to have a break for 2 seconds 
DISPLAY=:3 wine WoW.exe -opengl &  # Launches WoW

but i got this input in the terminal:

```
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux oliver-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.3.log", Time: Mon Oct  6 20:00:26 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "ddc" already built-in
(II) Module "ramdac" already built-in
(EE) fglrx(0): [agp] Failed to set AGP mode!
(EE) fglrx(0): cannot init AGP
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(EE) fglrx(0): XMM failed to open CMMQS connection.
oliver@oliver-desktop:~$ wine: /home/oliver/.wine is not owned by you
[glesx] __glESXExtensionInit: No GL ES2.0 capable screen found!
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
(EE) fglrx(0): PPLIB: PPLIB is not initialized!.
(EE) fglrx(0): PPLIB: swlPPLibNotifyEventToPPLib() failed!
(EE) fglrx(0):        ulEventType = 0000000c, ulEventData = 00000001
(EE) fglrx(0): PPLIB: PPLIB is not initialized!.
(EE) fglrx(0): PPLIB: swlPPLibNotifyEventToPPLib() failed!
(EE) fglrx(0):        ulEventType = 00000002, ulEventData = 00000000
(EE) fglrx(0): firegl_SetSuspendResumeState FAILED -1003.
~~

```

---

### Post by Eviljim on 2008-10-06
Where are the Warcraft files located?

Are they on a Windows NTFS partition, or are they installed in the Wine drive_c folder?

They should be in the Wine drive_c/Program files/World of Warcraft folder for it to really run properly.

Are you sure you have added the line SET glxAPI "OpenGL" to the config.wtf because if not, the game will run in Direct 3d mode, which does not run well with the ATi driver.

Ati drivers however do support OpenGL.

The white minimap is a common problem for people who use ATi cards as the drivers do not support the use of pbuffers, which are required for the minimap to work. There is no workround for this.

Cheers.

---

### Post by Omeil on 2008-10-07
Gday again,

:D thanks for the support peoples, wow is located in my /home/oliver/games/wow/ directory so on my linux partition ext3 but not specifically in the wine folder. could this be a problem? as for the opengl yup checked its in there. Thanks for clarifying the minimap thing :).

---

