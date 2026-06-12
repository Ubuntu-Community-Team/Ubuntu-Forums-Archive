---
title: "fglrx + amd64 + X300 == signal 11"
date: 2007-05-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by caulfield14 on 2007-05-03
Hi everyone,

Getting no love when starting X after having installed the latest fglrx drivers. Can't find anyone having a similar issue. I followed the directions in the [BinaryDriverHowto]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") and X just hangs with a signal 11 error.

Any help appreciated. I'm new to Ubuntu and the proprietary ATI drivers, but not to X and unix. I'm jonesing for a dual-head setup, and it seems the open-source drivers can't deliver that on my onboard Radeon X300.

TIA,
Graham.


Xorg.0.log:
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux 347-gbakay-ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May  3 15:32:24 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies Inc RS482 [Radeon Xpress 200]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7a16e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,5950 card 103c,280a rev 10 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,5a3f card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 1002,5a39 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:12:0: chip 1002,4380 card 103c,2812 rev 00 class 01,06,01 hdr 00
(II) PCI: 00:13:0: chip 1002,4387 card 103c,280a rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4388 card 103c,280a rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4389 card 103c,280a rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:3: chip 1002,438a card 103c,280a rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:4: chip 1002,438b card 103c,280a rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:5: chip 1002,4386 card 103c,280a rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4385 card 103c,280a rev 13 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,438c card 103c,280a rev 00 class 01,01,8f hdr 00
(II) PCI: 00:14:2: chip 1002,4383 card 103c,280a rev 00 class 04,03,00 hdr 00
(II) PCI: 00:14:3: chip 1002,438d card 103c,280a rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4384 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:05:0: chip 1002,5974 card 103c,280a rev 00 class 03,00,00 hdr 80
(II) PCI: 01:05:1: chip 1002,5874 card 103c,280b rev 00 class 03,80,00 hdr 00
(II) PCI: 3f:00:0: chip 14e4,167b card 103c,280a rev 02 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,63), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00001000 - 0x00001fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd8500000 - 0xd87fffff (0x300000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc8000000 - 0xd81fffff (0x10200000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 63: bridge is at (0:7:0), (0,63,63), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 63 non-prefetchable memory range:
	[0] -1	0	0xd8200000 - 0xd84fffff (0x300000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 7: bridge is at (0:20:4), (0,7,7), BCTRL: 0x0002 (VGA_EN is cleared)
(--) PCI:*(1:5:0) ATI Technologies Inc RS482 [Radeon Xpress 200] rev 0, Mem @ 0xc8000000/27, 0xd8500000/16, I/O @ 0x1000/8
(--) PCI: (1:5:1) ATI Technologies Inc unknown chipset (0x5874) rev 0, Mem @ 0xd0000000/27, 0xd8510000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xd8400000 - 0xd840ffff (0x10000) MX[B]
	[1] -1	0	0xd8a00000 - 0xd8a03fff (0x4000) MX[B]
	[2] -1	0	0xd8a09400 - 0xd8a097ff (0x400) MX[B]
	[3] -1	0	0xd8a09800 - 0xd8a098ff (0x100) MX[B]
	[4] -1	0	0xd8a08000 - 0xd8a08fff (0x1000) MX[B]
	[5] -1	0	0xd8a07000 - 0xd8a07fff (0x1000) MX[B]
	[6] -1	0	0xd8a06000 - 0xd8a06fff (0x1000) MX[B]
	[7] -1	0	0xd8a05000 - 0xd8a05fff (0x1000) MX[B]
	[8] -1	0	0xd8a04000 - 0xd8a04fff (0x1000) MX[B]
	[9] -1	0	0xd8a09000 - 0xd8a093ff (0x400) MX[B]
	[10] -1	0	0xd8510000 - 0xd851ffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xd8500000 - 0xd850ffff (0x10000) MX[B](B)
	[13] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[14] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
	[15] -1	0	0x0000205c - 0x0000205f (0x4) IX[B]
	[16] -1	0	0x00002048 - 0x0000204f (0x8) IX[B]
	[17] -1	0	0x00002058 - 0x0000205b (0x4) IX[B]
	[18] -1	0	0x00002040 - 0x00002047 (0x8) IX[B]
	[19] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[20] -1	0	0x00002000 - 0x0000200f (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001000 - 0x000010ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd8400000 - 0xd840ffff (0x10000) MX[B]
	[1] -1	0	0xd8a00000 - 0xd8a03fff (0x4000) MX[B]
	[2] -1	0	0xd8a09400 - 0xd8a097ff (0x400) MX[B]
	[3] -1	0	0xd8a09800 - 0xd8a098ff (0x100) MX[B]
	[4] -1	0	0xd8a08000 - 0xd8a08fff (0x1000) MX[B]
	[5] -1	0	0xd8a07000 - 0xd8a07fff (0x1000) MX[B]
	[6] -1	0	0xd8a06000 - 0xd8a06fff (0x1000) MX[B]
	[7] -1	0	0xd8a05000 - 0xd8a05fff (0x1000) MX[B]
	[8] -1	0	0xd8a04000 - 0xd8a04fff (0x1000) MX[B]
	[9] -1	0	0xd8a09000 - 0xd8a093ff (0x400) MX[B]
	[10] -1	0	0xd8510000 - 0xd851ffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xd8500000 - 0xd850ffff (0x10000) MX[B](B)
	[13] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[14] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
	[15] -1	0	0x0000205c - 0x0000205f (0x4) IX[B]
	[16] -1	0	0x00002048 - 0x0000204f (0x8) IX[B]
	[17] -1	0	0x00002058 - 0x0000205b (0x4) IX[B]
	[18] -1	0	0x00002040 - 0x00002047 (0x8) IX[B]
	[19] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[20] -1	0	0x00002000 - 0x0000200f (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001000 - 0x000010ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd8400000 - 0xd840ffff (0x10000) MX[B]
	[5] -1	0	0xd8a00000 - 0xd8a03fff (0x4000) MX[B]
	[6] -1	0	0xd8a09400 - 0xd8a097ff (0x400) MX[B]
	[7] -1	0	0xd8a09800 - 0xd8a098ff (0x100) MX[B]
	[8] -1	0	0xd8a08000 - 0xd8a08fff (0x1000) MX[B]
	[9] -1	0	0xd8a07000 - 0xd8a07fff (0x1000) MX[B]
	[10] -1	0	0xd8a06000 - 0xd8a06fff (0x1000) MX[B]
	[11] -1	0	0xd8a05000 - 0xd8a05fff (0x1000) MX[B]
	[12] -1	0	0xd8a04000 - 0xd8a04fff (0x1000) MX[B]
	[13] -1	0	0xd8a09000 - 0xd8a093ff (0x400) MX[B]
	[14] -1	0	0xd8510000 - 0xd851ffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xd8500000 - 0xd850ffff (0x10000) MX[B](B)
	[17] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
	[21] -1	0	0x0000205c - 0x0000205f (0x4) IX[B]
	[22] -1	0	0x00002048 - 0x0000204f (0x8) IX[B]
	[23] -1	0	0x00002058 - 0x0000205b (0x4) IX[B]
	[24] -1	0	0x00002040 - 0x00002047 (0x8) IX[B]
	[25] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[26] -1	0	0x00002000 - 0x0000200f (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00001000 - 0x000010ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.36.5
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.36.5
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.36g1                           
(II) ATI Proprietary Linux Driver Build Date: Apr 17 2007 10:04:46
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.36.1.1.2.3-driver-lnx-x86-x86_64-338188
(WW) fglrx: No matching Device section for instance (BusID PCI:1:5:1) found
(--) Chipset Supported AMD Graphics Processor (0x5974) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd8400000 - 0xd840ffff (0x10000) MX[B]
	[5] -1	0	0xd8a00000 - 0xd8a03fff (0x4000) MX[B]
	[6] -1	0	0xd8a09400 - 0xd8a097ff (0x400) MX[B]
	[7] -1	0	0xd8a09800 - 0xd8a098ff (0x100) MX[B]
	[8] -1	0	0xd8a08000 - 0xd8a08fff (0x1000) MX[B]
	[9] -1	0	0xd8a07000 - 0xd8a07fff (0x1000) MX[B]
	[10] -1	0	0xd8a06000 - 0xd8a06fff (0x1000) MX[B]
	[11] -1	0	0xd8a05000 - 0xd8a05fff (0x1000) MX[B]
	[12] -1	0	0xd8a04000 - 0xd8a04fff (0x1000) MX[B]
	[13] -1	0	0xd8a09000 - 0xd8a093ff (0x400) MX[B]
	[14] -1	0	0xd8510000 - 0xd851ffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xd8500000 - 0xd850ffff (0x10000) MX[B](B)
	[17] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
	[21] -1	0	0x0000205c - 0x0000205f (0x4) IX[B]
	[22] -1	0	0x00002048 - 0x0000204f (0x8) IX[B]
	[23] -1	0	0x00002058 - 0x0000205b (0x4) IX[B]
	[24] -1	0	0x00002040 - 0x00002047 (0x8) IX[B]
	[25] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[26] -1	0	0x00002000 - 0x0000200f (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00001000 - 0x000010ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x7c7c70
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd8400000 - 0xd840ffff (0x10000) MX[B]
	[5] -1	0	0xd8a00000 - 0xd8a03fff (0x4000) MX[B]
	[6] -1	0	0xd8a09400 - 0xd8a097ff (0x400) MX[B]
	[7] -1	0	0xd8a09800 - 0xd8a098ff (0x100) MX[B]
	[8] -1	0	0xd8a08000 - 0xd8a08fff (0x1000) MX[B]
	[9] -1	0	0xd8a07000 - 0xd8a07fff (0x1000) MX[B]
	[10] -1	0	0xd8a06000 - 0xd8a06fff (0x1000) MX[B]
	[11] -1	0	0xd8a05000 - 0xd8a05fff (0x1000) MX[B]
	[12] -1	0	0xd8a04000 - 0xd8a04fff (0x1000) MX[B]
	[13] -1	0	0xd8a09000 - 0xd8a093ff (0x400) MX[B]
	[14] -1	0	0xd8510000 - 0xd851ffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xd8500000 - 0xd850ffff (0x10000) MX[B](B)
	[17] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
	[24] -1	0	0x0000205c - 0x0000205f (0x4) IX[B]
	[25] -1	0	0x00002048 - 0x0000204f (0x8) IX[B]
	[26] -1	0	0x00002058 - 0x0000205b (0x4) IX[B]
	[27] -1	0	0x00002040 - 0x00002047 (0x8) IX[B]
	[28] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[29] -1	0	0x00002000 - 0x0000200f (0x10) IX[B]
	[30] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[31] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[32] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x00001000 - 0x000010ff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "ATI Radeon Xpress Series" (Chipset = 0x5974)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x280a)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc8000000
(--) fglrx(0): MMIO registers at 0xd8500000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON XPRESS 200 Series
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: RS48
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.36.5
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0):  Display1: No EDID information from DDC.
(II) fglrx(0):  Display1: Failed to get EDID information. 
(II) fglrx(0): Connected Display2: DFP on external TMDS [tmds2]
(II) fglrx(0): Display2 EDID data ---------------------------
(II) fglrx(0): Manufacturer: GSM  Model: 4ae2  Serial#: 67616
(II) fglrx(0): Year: 2006  Week: 7
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.647 redY: 0.346   greenX: 0.292 greenY: 0.602
(II) fglrx(0): blueX: 0.149 blueY: 0.130   whiteX: 0.313 whiteY: 0.328
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 75  vid: 20273
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 71 kHz, PixClock max 110 MHz
(II) fglrx(0): Monitor name: L1952TX
(II) fglrx(0): Monitor name: 
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff001e6de24a20080100
(II) fglrx(0): 	07100103ea261e78eaec54a5584a9a26
(II) fglrx(0): 	215054a56a80314f454f614f81800101
(II) fglrx(0): 	010101010101302a009851002a403070
(II) fglrx(0): 	1300782d1100001e000000fd00384b1e
(II) fglrx(0): 	470b000a202020202020000000fc004c
(II) fglrx(0): 	3139353254580a2020202020000000fc
(II) fglrx(0): 	000a2020202020202020202020200030
(II) fglrx(0): End of Display2 EDID data --------------------
(II) fglrx(0): Primary Controller - DFP on external TMDS
(II) fglrx(0): Secondary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 401/401MHz @ 50Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 14 modes found for primary display.
(--) fglrx(0): Virtual size is 1024x768 (pitch 0)
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x6d) [0x48282d]
1: /lib/libc.so.6 [0x2b4c32d9dd40]
2: /usr/lib/xorg/modules/drivers//fglrx_drv.so(swlDalHelperValidateModeFromDAL+0x549) [0x2b4c34dbcd29]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x2b4c34d9d70e]
4: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPreInit+0x877) [0x2b4c34d98e37]
5: /usr/X11R6/bin/X(InitOutput+0x9bc) [0x4657ec]
6: /usr/X11R6/bin/X(main+0x275) [0x436e55]
7: /lib/libc.so.6(__libc_start_main+0xf4) [0x2b4c32d8a8e4]
8: /usr/X11R6/bin/X(FontFileCompleteXLFD+0x241) [0x436339]

Fatal server error:
Caught signal 11.  Server aborting

```

xorg.conf:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RS482 [Radeon Xpress 200]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS482 [Radeon Xpress 200]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

```

---

### Post by NickK1066 on 2007-05-03
(WW) fglrx: No matching Device section for instance (BusID PCI:1:5:1) found

This is an interesting line. It's indicating that the X system isn't finding the configured device.

I would comment out the PCI bus ID line from the Xorg.conf and try that.

Also that conf only has one display configured.

I've not yet used my X1950XTX with dual monitors. So I can't help further :/

---

### Post by caulfield14 on 2007-05-03
No dice, I'm afraid. Same problem. Although now I'm wondering why I'm getting that message. Using that Busid works for the radeon driver.

I haven't put in a config for my other monitor yet. I want to get one working first :)

---

### Post by NickK1066 on 2007-05-04
Hmm it took me 3 days to get the 1950 working :/ First to get into X, next to get it supporting OpenGL in hardware.

Hmm as you've not got an X session I don't think flgrxinfo will return anything useful.

Have you compiled the new drivers into the restricted set of drivers?

I noticed that the new drivers were not being picked up; instead only the restricted ones were. After rebuilding the restricted set to add the new drivers the whole things worked.

The guide I used, eventually, is here: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
I had todo Method 2.

---

### Post by caulfield14 on 2007-05-04
Yeah, I went through that guide. Just tried it again, in fact. No luck.

My kern.log says [fglrx] module loaded. But I still get a black screen when starting X and the Signal 11 in the Xorg log.

---

