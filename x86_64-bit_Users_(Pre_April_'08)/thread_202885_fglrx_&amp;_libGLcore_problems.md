---
title: "fglrx &amp; libGLcore problems"
date: 2006-06-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by z3r0x on 2006-06-24
Hi @ all
I tried to update xorg and now X wont start.

```


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15-ubuntu1 x86_64
Current Operating System: Linux TheMentor 2.6.15-25-amd64-generic #1 SMP PREEMPT Wed Jun 14 11:28:03 UTC 2006 x86_64
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun 24 13:42:16 2006
(==) Using config file: "/home/unix/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Intel Corporation 82852/855GM Integrated Graphics Device"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,005e card 1043,815a rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1043,815a rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1043,815a rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1043,815a rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1043,815a rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0059 card 1043,812a rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,0053 card 1043,815a rev f2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,0054 card 1043,815a rev f3 class 01,01,85 hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 1043,815a rev f3 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0a:0: chip 10de,0057 card 1043,8141 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1002,5d52 card 1002,0b12 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,5d72 card 1002,0b13 rev 00 class 03,80,00 hdr 00
(II) PCI: 05:0a:0: chip 1095,3114 card 1043,8167 rev 02 class 01,04,00 hdr 00
(II) PCI: 05:0b:0: chip 104c,8023 card 1043,808b rev 00 class 0c,00,10 hdr 00
(II) PCI: 05:0c:0: chip 11ab,4320 card 1043,811a rev 13 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:9:0), (0,5,5), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x00008000 - 0x00009fff (0x2000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x500fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:11:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:13:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:14:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc R480 [Radeon X850XT (PCIE)] (Primary) rev 0, Mem @ 0xc0000000/28, 0xd1000000/16, I/O @ 0xa000/8
(--) PCI: (1:0:1) ATI Technologies Inc R480 [Radeon X850XT (PCIE)] (Secondary) rev 0, Mem @ 0xd1010000/16
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
	[0] -1	0	0xd3004000 - 0xd3007fff (0x4000) MX[B]
	[1] -1	0	0xd3000000 - 0xd3003fff (0x4000) MX[B]
	[2] -1	0	0xd3009000 - 0xd30097ff (0x800) MX[B]
	[3] -1	0	0xd3008000 - 0xd30083ff (0x400) MX[B]
	[4] -1	0	0xd4000000 - 0xd4000fff (0x1000) MX[B]
	[5] -1	0	0xd4001000 - 0xd4001fff (0x1000) MX[B]
	[6] -1	0	0xd4002000 - 0xd4002fff (0x1000) MX[B]
	[7] -1	0	0xd4003000 - 0xd4003fff (0x1000) MX[B]
	[8] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[9] -1	0	0xd4004000 - 0xd4004fff (0x1000) MX[B]
	[10] -1	0	0xd1000000 - 0xd100ffff (0x10000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[13] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[14] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[15] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[16] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[17] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[18] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[20] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[21] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[22] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[23] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[25] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[26] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[27] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[28] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[31] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[32] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[33] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[34] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[35] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xd1010000 - 0xd101ffff (0x10000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd3004000 - 0xd3007fff (0x4000) MX[B]
	[1] -1	0	0xd3000000 - 0xd3003fff (0x4000) MX[B]
	[2] -1	0	0xd3009000 - 0xd30097ff (0x800) MX[B]
	[3] -1	0	0xd3008000 - 0xd30083ff (0x400) MX[B]
	[4] -1	0	0xd4000000 - 0xd4000fff (0x1000) MX[B]
	[5] -1	0	0xd4001000 - 0xd4001fff (0x1000) MX[B]
	[6] -1	0	0xd4002000 - 0xd4002fff (0x1000) MX[B]
	[7] -1	0	0xd4003000 - 0xd4003fff (0x1000) MX[B]
	[8] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[9] -1	0	0xd4004000 - 0xd4004fff (0x1000) MX[B]
	[10] -1	0	0xd1000000 - 0xd100ffff (0x10000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[13] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[14] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[15] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[16] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[17] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[18] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[20] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[21] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[22] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[23] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[25] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[26] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[27] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[28] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[31] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[32] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[33] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[34] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[35] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xd1010000 - 0xd101ffff (0x10000) MX[B](B)
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
	[4] -1	0	0xd3004000 - 0xd3007fff (0x4000) MX[B]
	[5] -1	0	0xd3000000 - 0xd3003fff (0x4000) MX[B]
	[6] -1	0	0xd3009000 - 0xd30097ff (0x800) MX[B]
	[7] -1	0	0xd3008000 - 0xd30083ff (0x400) MX[B]
	[8] -1	0	0xd4000000 - 0xd4000fff (0x1000) MX[B]
	[9] -1	0	0xd4001000 - 0xd4001fff (0x1000) MX[B]
	[10] -1	0	0xd4002000 - 0xd4002fff (0x1000) MX[B]
	[11] -1	0	0xd4003000 - 0xd4003fff (0x1000) MX[B]
	[12] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[13] -1	0	0xd4004000 - 0xd4004fff (0x1000) MX[B]
	[14] -1	0	0xd1000000 - 0xd100ffff (0x10000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xd1010000 - 0xd101ffff (0x10000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[20] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[21] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[22] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[23] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[24] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[27] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[28] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[29] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[30] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[31] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[32] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[33] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[34] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[35] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[36] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[37] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[38] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[39] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[40] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[41] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[42] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(II) UnloadModule: "GLcore"
(EE) Failed to load module "GLcore" (loader failed, 7)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
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
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers/i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
	915GM, 945G, 945GM
(II) Primary Device is: PCI 01:00:0
(EE) No devices detected.

Fatal server error:
no screens found

```

this is my xorg.conf

```

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

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"GLcore"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ch"
	Option		"XkbVariant"	"de"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X850 XT (R480)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X850 XT (R480)"
	Monitor		"Standardbildschirm"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

does anybody know how to fix this problem?

---

### Post by Kilz on 2006-06-24
Have you tried this?
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by z3r0x on 2006-06-24
[QUOTE=Kilz]Have you tried this?
```
sudo dpkg-reconfigure xserver-xorg
```[/QUOTE]

sure many times

---

### Post by Xamusk on 2006-06-24
are you really sure your graphics card is an ATI one? you error mentions an Intel i810 device.
If you try to use the fglrx driver in a non-ati card, of course it won't work. If I do remember correctly, the driver for the i810 boards is "i810".
You can probably find out which card you have by using the **[FONT="Courier New"]lspci[/FONT]** command. Mine gave me this line in particular:
```
0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
```

---

### Post by z3r0x on 2006-06-24
[QUOTE=Xamusk]are you really sure your graphics card is an ATI one? you error mentions an Intel i810 device.
If you try to use the fglrx driver in a non-ati card, of course it won't work. If I do remember correctly, the driver for the i810 boards is "i810".
You can probably find out which card you have by using the **[FONT="Courier New"]lspci[/FONT]** command. Mine gave me this line in particular:
```
0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
```[/QUOTE]

;) sure it's an ati card

output of lspci

```

0000:01:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850XT (PCIE)] (Primary)

```

---

### Post by TD-Linux on 2006-06-27
I have this same exact problem, after updating from Breezy to Dapper. My eth0 also dissapeared, so I haven't been able to mess with this too much yet.
The ATI fglrx 8.22.x drivers I have I know aren't compatable with 7.0.0. What version is yours? Does it work?

My error is exactly the same, but it complains about a lack of the 'fglrx' module also.

Wow, nice graphics card. I have a Radeon X700PRO PCIE, if anyone cares.

Oh, and forgot to mention, I'm running 32-bit Kubuntu 6.06. So it isn't just a 64-bit issue, probably.

---

