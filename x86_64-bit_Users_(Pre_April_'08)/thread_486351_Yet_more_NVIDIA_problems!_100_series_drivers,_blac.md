---
title: "Yet more NVIDIA problems! 100 series drivers, black screen. :("
date: 2007-06-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by AnObfuscator on 2007-06-27
Hi;

I'm having very similar problems to [this thread]("http://ubuntuforums.org/showthread.php?t=484455"). However, the solutions there don't work for me at all.

I've tried the ubuntu restricted drivers manager, Envy, and Automatix, but none have worked. I've searched forums and google for alternate ways to install the drivers. I tried installing the newest nvidia package itself, but that hasn't worked.

I'm running kernel 16 generic, and I purged 15 off my system. 

When I try "startx" from root (via the troubleshooting GRUB entry), I get a black screen, and the system becomes unresponsive -- I assume the input devices are no longer loaded. When I try to boot the normal kernel, I get dumped to a console. X gives me this log:

```


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux Daedalus 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun 27 22:24:55 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Nvidia GeForce 6600 Gt"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/usr/share/fonts/X11/misc,
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
(**) Extension "Composite" is enabled
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,00e1 card 0000,0000 rev a1 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,00e0 card 1458,0c11 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,00e4 card 1458,0c11 rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,00e7 card 1458,5004 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,00e7 card 1458,5004 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,00e8 card 1458,5004 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:05:0: chip 10de,00df card 1458,e000 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:06:0: chip 10de,00ea card 1458,a002 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,00e5 card 1458,5002 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0a:0: chip 10de,00e3 card 1458,b002 rev a2 class 01,01,85 hdr 00
(II) PCI: 00:0b:0: chip 10de,00e2 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,00ed card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,00f1 card 1458,3150 rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:11:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf2000000 - 0xf4ffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:14:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(--) PCI:*(1:0:0) nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] rev 162, Mem @ 0xf2000000/24, 0xe0000000/28, 0xf3000000/24
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
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf1ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf5002000 - 0xf5002fff (0x1000) MX[B]
	[1] -1	0	0xf5001000 - 0xf5001fff (0x1000) MX[B]
	[2] -1	0	0xf5000000 - 0xf50000ff (0x100) MX[B]
	[3] -1	0	0xf5005000 - 0xf5005fff (0x1000) MX[B]
	[4] -1	0	0xf5004000 - 0xf5004fff (0x1000) MX[B]
	[5] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[6] -1	0	0xf3000000 - 0xf3ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[10] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[11] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[12] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[13] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[14] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[15] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[16] -1	0	0x0000a400 - 0x0000a47f (0x80) IX[B]
	[17] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[18] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[19] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[20] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[21] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf5002000 - 0xf5002fff (0x1000) MX[B]
	[1] -1	0	0xf5001000 - 0xf5001fff (0x1000) MX[B]
	[2] -1	0	0xf5000000 - 0xf50000ff (0x100) MX[B]
	[3] -1	0	0xf5005000 - 0xf5005fff (0x1000) MX[B]
	[4] -1	0	0xf5004000 - 0xf5004fff (0x1000) MX[B]
	[5] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[6] -1	0	0xf3000000 - 0xf3ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[10] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[11] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[12] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[13] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[14] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[15] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[16] -1	0	0x0000a400 - 0x0000a47f (0x80) IX[B]
	[17] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[18] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[19] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[20] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[21] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
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
	[4] -1	0	0xf5002000 - 0xf5002fff (0x1000) MX[B]
	[5] -1	0	0xf5001000 - 0xf5001fff (0x1000) MX[B]
	[6] -1	0	0xf5000000 - 0xf50000ff (0x100) MX[B]
	[7] -1	0	0xf5005000 - 0xf5005fff (0x1000) MX[B]
	[8] -1	0	0xf5004000 - 0xf5004fff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xf3000000 - 0xf3ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[16] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[17] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[18] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[19] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[20] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[21] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[22] -1	0	0x0000a400 - 0x0000a47f (0x80) IX[B]
	[23] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[24] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[25] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[26] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[27] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
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
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.11  Wed Jun 13 17:16:40 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
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
(II) NVIDIA dlloader X Driver  100.14.11  Wed Jun 13 16:35:28 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf5002000 - 0xf5002fff (0x1000) MX[B]
	[5] -1	0	0xf5001000 - 0xf5001fff (0x1000) MX[B]
	[6] -1	0	0xf5000000 - 0xf50000ff (0x100) MX[B]
	[7] -1	0	0xf5005000 - 0xf5005fff (0x1000) MX[B]
	[8] -1	0	0xf5004000 - 0xf5004fff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xf3000000 - 0xf3ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[16] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[17] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[18] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[19] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[20] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[21] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[22] -1	0	0x0000a400 - 0x0000a47f (0x80) IX[B]
	[23] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[24] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[25] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[26] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[27] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf5002000 - 0xf5002fff (0x1000) MX[B]
	[5] -1	0	0xf5001000 - 0xf5001fff (0x1000) MX[B]
	[6] -1	0	0xf5000000 - 0xf50000ff (0x100) MX[B]
	[7] -1	0	0xf5005000 - 0xf5005fff (0x1000) MX[B]
	[8] -1	0	0xf5004000 - 0xf5004fff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xf3000000 - 0xf3ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[19] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[20] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[21] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[22] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[23] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[24] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[25] -1	0	0x0000a400 - 0x0000a47f (0x80) IX[B]
	[26] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[27] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[28] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[29] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[30] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NvAGP" "1"
(**) NVIDIA(0): Option "RenderAccel" "True"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "LeftOf"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(WW) NVIDIA(0): No TwinView "MetaModes" specified; will fall back to Display
(WW) NVIDIA(0):     SubSection modes.
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): Use of NVIDIA internal AGP requested
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

Here is my xorg.conf: 
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Wed Jun 13 16:54:14 PDT 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Nvidia GeForce 6600 Gt"
    Driver         "nvidia"
    Option "NvAGP" "1"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Nvidia GeForce 6600 Gt"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "LeftOf"
    Option         "RenderAccel" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```

---

### Post by kuja on 2007-06-27
Is there any reason you must have the lastest 100 series drivers? With an older card like the 6600gt the nvidia-glx-new (which installs 1.0.9755 IIRC) package from the repositories should work fine.

---

### Post by AnObfuscator on 2007-06-27
Yeah, heh. 

The 96 drivers installed fine in 32bit, so I know the card itself is fine.
 Howeve, they won't in 64bit. Since I'm upgrading my system to a dual-core X2 w/ 4 gigs of ram and an 8600GT (ordered it Tuesday! on track to be here Friday!), I need both 64bit (to address my ram) and the 100 series driver (for the 8600GT). So, I figured I'd learn how to setup the drivers  I'm going to need, beforehand, so that the transfer goes relatively smoothly.

---

### Post by Hibbelharry on 2007-07-04
most likely your problem is if you install a newer nvidia driver, you have to remove the older nvidia kernel modules. they are located in /lib/modules/[kernelversion]/volatile. remove them, then depmod -ae to rebuild module dependencys. then it's time to reload your nvidia module by doing a rmmod nvidia;modprobe nvidia. you have to remove them again after each update of your restricted-modules package.

Hope this helps.

Greetz
Hibbelharry

---

