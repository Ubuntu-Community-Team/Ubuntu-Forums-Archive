---
title: "[SOLVED] The Settlers 3 crashes X. Why?"
date: 2007-11-04
forum: Wine
---

### Post by Benedolt on 2007-11-04
Hello everyone!

Nostalgia overcame me, so I installed my old copy of The Settlers III according to wine's [appdb entry]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4826").

I got it running that way and was even able to play an entire campaign. So apparently it works! Unfortunately the game crashes X after playing the intro movie in about 80% of the cases. This is really annoying. 

/EDIT: System is a Dell Inspiron E1505, with an Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller. Driver is the i810.

Does anyone have an idea how to fix this? Or can anyone read something from the logs:

xinit -- :1 -ac -depth 16 outputs:
```


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux angelo 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sun Nov  4 19:45:21 2007
(==) Using config file: "/etc/X11/xorg.conf"
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(EE) intel(0): [dri] DRIScreenInit failed. Disabling DRI.
(EE) AIGLX: Screen 0 is not DRI capable
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

Backtrace:
0: X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: /usr/lib/xorg/modules/drivers//i810_drv.so [0xb7b3154e]
3: /usr/lib/xorg/modules/drivers//i810_drv.so(intel_xf86CrtcSetMode+0x2c9) [0xb7b53239]
4: /usr/lib/xorg/modules/drivers//i810_drv.so(intel_xf86SetSingleMode+0x11a) [0xb7b533da]
5: /usr/lib/xorg/modules/drivers//i810_drv.so [0xb7b342a0]
6: /usr/lib/xorg/modules//libramdac.so [0xb79e1b38]
7: X [0x80cdff3]
8: X(xf86SwitchMode+0xce) [0x80c2d0e]
9: /usr/lib/xorg/modules/drivers//i810_drv.so(intel_xf86RandR12SetConfig+0x20c) [0xb7b559bc]
10: X [0x8159466]
11: X [0x81424ce]
12: X(Dispatch+0x19f) [0x808c61f]
13: X(main+0x495) [0x8074785]
14: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d0cebc]
15: X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error:
Caught signal 11.  Server aborting

xterm:  fatal IO error 32 (Broken pipe) or KillClient on X server ":1.0"

X connection to :1.0 broken (explicit kill or server shutdown).

xinit:  connection to X server lost.

```

And the game outputs:
```
fixme:win:EnumDisplayDevicesW ((null),0,0x33f1f0,0x00000000), stub!
fixme:d3d_surface:IWineD3DBaseSurfaceImpl_Blt Can't handle WINEDDBLT_ASYNC flag right now.
fixme:mciavi:MCIAVI_mciPlay Unsupported flag 01000003
X connection to :1.0 broken (explicit kill or server shutdown).

```

Thanks for your help!

---

### Post by Benedolt on 2007-12-12
As a workaround I disabled the movies altogether using the configuration tool coming with the game. That did the trick for me.

---

### Post by KhaaL on 2007-12-12
Good job! make sure to post that information at [appdb]("http://appdb.winehq.org") ;)

---

### Post by Xuewen on 2008-09-16
Thank you. One of my Chinese friends is just looking for this methord you wrote here. I will translate you post in [chinese translation](http://www.yongsfy.com/) version for him. Thanks again!

---

