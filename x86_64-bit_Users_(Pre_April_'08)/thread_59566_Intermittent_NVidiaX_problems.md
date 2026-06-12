---
title: "Intermittent NVidia/X problems"
date: 2005-08-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by mcguirk on 2005-08-24
I'm using the 7676 build of the AMD64 Nvidia graphics drivers (from their webpage) installed from their .run file (The nvidia-glx .deb packages gave me some screen corruption and didn't let me use most of my laptop's screen resolutions). And sometimes while booting (not all the time, maybe about 40%), X crashes and I get dropped to the command line.

I can fix this by reinstalling the NVidia drivers but its really terribly inconvienent.

Anyone have any ideas how to permanently fix this?

What follows is the Xorg error log I get when starting up.

Thanks guys!

---

### Post by mcguirk on 2005-08-24
X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154247 root@)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 x86_64 [ELF] 
Current Operating System: Linux mcguirklaptop 2.6.10-5-amd64-generic #1 Tue Apr 5 12:21:57 UTC 2005 x86_64
Build Date: 05 April 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-amd64-generic (buildd@king) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:21:57 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 24 08:15:21 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV17 [GeForce4 420 Go 32M]"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc104"
(**) XKB: model: "pc104"
(**) Option "XkbLayout" "us"
(**) XKB: layout: "us"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/usr/lib/X11/fonts/misc,/usr/lib/X11/fonts/100dpi/:unscaled,/usr/lib/X11/fonts/75dpi/:unscaled,/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/100dpi,/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,00d1 card 0000,0000 rev a4 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,00d0 card 10de,0c80 rev a6 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,00d4 card 103c,006d rev a4 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,00d7 card 10de,0c80 rev a5 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,00d7 card 10de,0c80 rev a5 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,00d8 card 10de,0c80 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:06:0: chip 10de,00da card 103c,006d rev a2 class 04,01,00 hdr 80
(II) PCI: 00:06:1: chip 10de,00d9 card 103c,006d rev a2 class 07,03,00 hdr 80
(II) PCI: 00:08:0: chip 10de,00d5 card 10de,0c80 rev a5 class 01,01,8a hdr 00
(II) PCI: 00:0a:0: chip 10de,00dd card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0b:0: chip 10de,00d2 card 0000,0000 rev a4 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0176 card 103c,006d rev a3 class 03,00,00 hdr 00
(II) PCI: 02:01:0: chip 10ec,8139 card 103c,006b rev 10 class 02,00,00 hdr 00
(II) PCI: 02:02:0: chip 14e4,4320 card 103c,12f4 rev 03 class 02,80,00 hdr 00
(II) PCI: 02:04:0: chip 104c,ac54 card 4000,0000 rev 01 class 06,07,00 hdr 82
(II) PCI: 02:04:1: chip 104c,ac54 card 6000,0000 rev 01 class 06,07,00 hdr 82
(II) PCI: 02:04:2: chip 104c,8201 card 103c,006d rev 01 class 08,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:10:0), (0,2,2), BCTRL: 0x0200 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00003000 - 0x00007fff (0x5000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xe8100000 - 0xe97fffff (0x1700000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:11:0), (0,1,1), BCTRL: 0x000f (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xea000000 - 0xeaffffff (0x1000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xfc0fffff (0x4100000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:0), (-1,-1,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:1), (-1,-1,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:2), (-1,-1,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:3), (-1,-1,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:4:0), (2,3,6), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xe8400000 - 0xe85fffff (0x200000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 7: bridge is at (2:4:1), (2,7,10), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 7 I/O range:
	[0] -1	0	0x00006000 - 0x00006fff (0x1000) IX[B]
	[1] -1	0	0x00005000 - 0x00005fff (0x1000) IX[B]
(II) Bus 7 non-prefetchable memory range:
	[0] -1	0	0xe8c00000 - 0xe8ffffff (0x400000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV17 [GeForce4 420 Go 32M] rev 163, Mem @ 0xea000000/24, 0xf8000000/26, 0xfc000000/19
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe8100000 - 0xe8101fff (0x2000) MX[B]
	[1] -1	0	0xe8104000 - 0xe81040ff (0x100) MX[B]
	[2] -1	0	0xe8003000 - 0xe8003fff (0x1000) MX[B]
	[3] -1	0	0xe8002000 - 0xe8002fff (0x1000) MX[B]
	[4] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[5] -1	0	0xe8001000 - 0xe8001fff (0x1000) MX[B]
	[6] -1	0	0xe8000000 - 0xe8000fff (0x1000) MX[B]
	[7] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[8] -1	0	0xfc000000 - 0xfc07ffff (0x80000) MX[B](B)
	[9] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[10] -1	0	0xea000000 - 0xeaffffff (0x1000000) MX[B](B)
	[11] -1	0	0x00007400 - 0x0000743f (0x40) IX[B]
	[12] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[13] -1	0	0x00002080 - 0x0000208f (0x10) IX[B]
	[14] -1	0	0x00001c80 - 0x00001cff (0x80) IX[B]
	[15] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[16] -1	0	0x00001c00 - 0x00001c7f (0x80) IX[B]
	[17] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[18] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[19] -1	0	0x00002040 - 0x0000207f (0x40) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe8100000 - 0xe8101fff (0x2000) MX[B]
	[1] -1	0	0xe8104000 - 0xe81040ff (0x100) MX[B]
	[2] -1	0	0xe8003000 - 0xe8003fff (0x1000) MX[B]
	[3] -1	0	0xe8002000 - 0xe8002fff (0x1000) MX[B]
	[4] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[5] -1	0	0xe8001000 - 0xe8001fff (0x1000) MX[B]
	[6] -1	0	0xe8000000 - 0xe8000fff (0x1000) MX[B]
	[7] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[8] -1	0	0xfc000000 - 0xfc07ffff (0x80000) MX[B](B)
	[9] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[10] -1	0	0xea000000 - 0xeaffffff (0x1000000) MX[B](B)
	[11] -1	0	0x00007400 - 0x0000743f (0x40) IX[B]
	[12] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[13] -1	0	0x00002080 - 0x0000208f (0x10) IX[B]
	[14] -1	0	0x00001c80 - 0x00001cff (0x80) IX[B]
	[15] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[16] -1	0	0x00001c00 - 0x00001c7f (0x80) IX[B]
	[17] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[18] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[19] -1	0	0x00002040 - 0x0000207f (0x40) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xe8100000 - 0xe8101fff (0x2000) MX[B]
	[6] -1	0	0xe8104000 - 0xe81040ff (0x100) MX[B]
	[7] -1	0	0xe8003000 - 0xe8003fff (0x1000) MX[B]
	[8] -1	0	0xe8002000 - 0xe8002fff (0x1000) MX[B]
	[9] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[10] -1	0	0xe8001000 - 0xe8001fff (0x1000) MX[B]
	[11] -1	0	0xe8000000 - 0xe8000fff (0x1000) MX[B]
	[12] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[13] -1	0	0xfc000000 - 0xfc07ffff (0x80000) MX[B](B)
	[14] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[15] -1	0	0xea000000 - 0xeaffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00007400 - 0x0000743f (0x40) IX[B]
	[19] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[20] -1	0	0x00002080 - 0x0000208f (0x10) IX[B]
	[21] -1	0	0x00001c80 - 0x00001cff (0x80) IX[B]
	[22] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[23] -1	0	0x00001c00 - 0x00001c7f (0x80) IX[B]
	[24] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[25] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[26] -1	0	0x00002040 - 0x0000207f (0x40) IX[B]
(II) LoadModule: "bitmap"

---

### Post by mcguirk on 2005-08-24
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension FontCache
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7676
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "nvidia"
(II) Loading /usr/X11R6/lib/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7676
	Module class: XFree86 Video Driver
(II) LoadModule: "keyboard"
(II) Loading /usr/X11R6/lib/modules/input/keyboard_drv.o
(II) Module keyboard: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) NVIDIA X Driver  1.0-7676  Fri Jul 29 13:17:34 PDT 2005
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xe8100000 - 0xe8101fff (0x2000) MX[B]
	[6] -1	0	0xe8104000 - 0xe81040ff (0x100) MX[B]
	[7] -1	0	0xe8003000 - 0xe8003fff (0x1000) MX[B]
	[8] -1	0	0xe8002000 - 0xe8002fff (0x1000) MX[B]
	[9] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[10] -1	0	0xe8001000 - 0xe8001fff (0x1000) MX[B]
	[11] -1	0	0xe8000000 - 0xe8000fff (0x1000) MX[B]
	[12] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[13] -1	0	0xfc000000 - 0xfc07ffff (0x80000) MX[B](B)
	[14] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[15] -1	0	0xea000000 - 0xeaffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00007400 - 0x0000743f (0x40) IX[B]
	[19] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[20] -1	0	0x00002080 - 0x0000208f (0x10) IX[B]
	[21] -1	0	0x00001c80 - 0x00001cff (0x80) IX[B]
	[22] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[23] -1	0	0x00001c00 - 0x00001c7f (0x80) IX[B]
	[24] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[25] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[26] -1	0	0x00002040 - 0x0000207f (0x40) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xe8100000 - 0xe8101fff (0x2000) MX[B]
	[6] -1	0	0xe8104000 - 0xe81040ff (0x100) MX[B]
	[7] -1	0	0xe8003000 - 0xe8003fff (0x1000) MX[B]
	[8] -1	0	0xe8002000 - 0xe8002fff (0x1000) MX[B]
	[9] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[10] -1	0	0xe8001000 - 0xe8001fff (0x1000) MX[B]
	[11] -1	0	0xe8000000 - 0xe8000fff (0x1000) MX[B]
	[12] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[13] -1	0	0xfc000000 - 0xfc07ffff (0x80000) MX[B](B)
	[14] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[15] -1	0	0xea000000 - 0xeaffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00007400 - 0x0000743f (0x40) IX[B]
	[22] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[23] -1	0	0x00002080 - 0x0000208f (0x10) IX[B]
	[24] -1	0	0x00001c80 - 0x00001cff (0x80) IX[B]
	[25] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[26] -1	0	0x00001c00 - 0x00001c7f (0x80) IX[B]
	[27] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[28] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[29] -1	0	0x00002040 - 0x0000207f (0x40) IX[B]
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xF8000000
(--) NVIDIA(0): MMIO registers at 0xEA000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce4 420 Go 32M
(--) NVIDIA(0): VideoBIOS: 04.17.20.49.25
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): VideoRAM: 32768 kBytes
(II) NVIDIA(0): Connected display device(s): DFP-0
(--) NVIDIA(0): DFP-0: maximum pixel clock: 224 MHz
(--) NVIDIA(0): DFP-0: Internal Single Link LVDS
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(WW) NVIDIA(0): config file hsync range 30-67kHz not within DDC hsync ranges.
(WW) NVIDIA(0): config file vrefresh range 30-60Hz not within DDC vrefresh ranges.
(II) NVIDIA(0): Generic Monitor: Using hsync range of 30.00-67.00 kHz
(II) NVIDIA(0): Generic Monitor: Using vrefresh range of 30.00-60.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 224.00 MHz
(II) NVIDIA(0): Not using default mode "640x350" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x175" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x400" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x200" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "720x400" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "360x200" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "512x384" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "512x384" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "512x384" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "576x432" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "832x624" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "416x312" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) NVIDIA(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x960" (height too large for virtual size)
(WW) NVIDIA(0): Not using mode "840x525" (height 1050 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 800)
(WW) NVIDIA(0): Not using mode "700x525" (height 1050 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 800)
(WW) NVIDIA(0): Not using mode "640x512" (height 1024 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 800)
(WW) NVIDIA(0): Not using mode "720x450" (height 900 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 800)
(WW) NVIDIA(0): Not using mode "640x480" (height 960 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 800)
(WW) NVIDIA(0): Not using mode "1152x768":
(WW) NVIDIA(0):   horizontal sync start (1178) not a multiple of 8
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device DFP-0:
(**) NVIDIA(0):      Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Mode "1280x800@60": 83.9 MHz, 50.7 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(++) NVIDIA(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfc000000 - 0xfc07ffff (0x80000) MX[B]
	[1] 0	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B]
	[2] 0	0	0xea000000 - 0xeaffffff (0x1000000) MX[B]
	[3] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[4] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xe8100000 - 0xe8101fff (0x2000) MX[B]
	[9] -1	0	0xe8104000 - 0xe81040ff (0x100) MX[B]
	[10] -1	0	0xe8003000 - 0xe8003fff (0x1000) MX[B]
	[11] -1	0	0xe8002000 - 0xe8002fff (0x1000) MX[B]
	[12] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[13] -1	0	0xe8001000 - 0xe8001fff (0x1000) MX[B]
	[14] -1	0	0xe8000000 - 0xe8000fff (0x1000) MX[B]
	[15] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[16] -1	0	0xfc000000 - 0xfc07ffff (0x80000) MX[B](B)
	[17] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[18] -1	0	0xea000000 - 0xeaffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00007400 - 0x0000743f (0x40) IX[B]
	[25] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[26] -1	0	0x00002080 - 0x0000208f (0x10) IX[B]
	[27] -1	0	0x00001c80 - 0x00001cff (0x80) IX[B]
	[28] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[29] -1	0	0x00001c00 - 0x00001c7f (0x80) IX[B]
	[30] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[31] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[32] -1	0	0x00002040 - 0x0000207f (0x40) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x800"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Fatal server error:
Caught signal 11.  Server aborting


Please consult the The X.Org Foundation support 
	 at [http://wiki.X.Org](http://wiki.X.Org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

---

### Post by tseliot on 2005-08-25
[QUOTE=mcguirk]I'm using the 7676 build of the AMD64 Nvidia graphics drivers (from their webpage) installed from their .run file (The nvidia-glx .deb packages gave me some screen corruption and didn't let me use most of my laptop's screen resolutions). And sometimes while booting (not all the time, maybe about 40%), X crashes and I get dropped to the command line.

I can fix this by reinstalling the NVidia drivers but its really terribly inconvienent.

Anyone have any ideas how to permanently fix this?

What follows is the Xorg error log I get when starting up.

Thanks guys![/QUOTE]
1) Try 7667 unless you have a Geforce 7800. 7676 is (more) buggy.

2) Please try my guide (follow EVERY step) if you want to install it

[http://www.ubuntuforums.org/showthread.php?t=57368](http://www.ubuntuforums.org/showthread.php?t=57368) 

3) Make sure your Graphic card is supported by the driver (you can find a list of the unsupported hardware in my guide)

---

### Post by bagatonovic on 2005-08-25
Actually I had this exact same problem.  Here's what I did to fix it.

1) sudo rm /etc/init.d/nvidia-glx
2) reinstall the driver
3) reboot

To verify we are having the same problem, when booting X crashes, and you are at terminal.  When you reinstall the driver, X wont start.  When you reboot, X will start.  When you reboot again, the problem happens again.  If this is what was happening to you, try the above.

---

### Post by mcguirk on 2005-08-25
Hm, not exactly.

It's more like occasionally when I reboot, X won't start so I'm dumped to the terminal.
Then when I reinstall the driver, X WILL start.

I'll give it a try though :)

---

### Post by bagatonovic on 2005-08-25
Yeah, either follow Tseliot's guide or what I said.  Either one will work.
Just FYI I am running 7676 stable.

---

