---
title: "[SOLVED] No desktop after upgrade to gutsy"
date: 2007-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by PaulRSte on 2007-11-18
I've just upgraded to Gutsy Gibbon from feisty fawn.  The upgrade looked to go fine and got through to the end, requiring  a reboot after the last stage of removing all redundant packages.

After the reboot though it does not boot into the desktop. It looks to be having a number of attempts to go into the desktop but then comes back to a tty login after failing to find a restart image, "No resume image, doing normal boot", which I assume is normal as I have not hibernated the system.

I can log in ok but if I then  try to "startx" I get the same attempts to go into the desktop but this time ending with a number of error messages such as:-

cannot open device /dev/input/wacom no such file or directory

could not init font path element /usr/share/fonts/x11/cyrillic, removing it from list

X10 fatal IO error 104

Can anyone help please?  More detail is available if required.

---

### Post by hangfire on 2007-11-18
Please post your **/var/log/Xorg.0.log** .

Also check to see if your **/etc/X11/xorg.conf** has a backup made by the upgrader. You could simply try swapping them out and see if it works better.

-HF

---

### Post by PaulRSte on 2007-11-19
Thanks for that hangfire.

Have tried swapping xorg.conf with xorg.conf.backup and rebooting but went exactly the same, so I'm posting Xorg.0.log from before I tried the backup config.


```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux PVR-1 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64
Build Date: 29 September 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 18 22:20:46 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation C51PV [GeForce 6150]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7cd8a0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(--) using VT number 10

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,02f0 card 1043,81c0 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 1043,81c0 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 1043,81c0 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 1043,81c0 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 1043,81c0 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 1043,81c0 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 1043,81c0 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 1043,81c0 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,02fc card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10de,02fd card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 10de,02fb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 10de,0240 card 1043,81cd rev a2 class 03,00,00 hdr 00
(II) PCI: 00:09:0: chip 10de,0270 card 1043,81c0 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0260 card 1043,81c0 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 1043,81c0 rev a3 class 0c,05,00 hdr 80
(II) PCI: 00:0a:2: chip 10de,0272 card 1043,81c0 rev a3 class 05,00,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 1043,81c0 rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 1043,81c0 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card 1043,81c0 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,0266 card 1043,81c0 rev a1 class 01,01,85 hdr 00
(II) PCI: 00:0f:0: chip 10de,0267 card 1043,81c0 rev a1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:1: chip 10de,026c card 1043,81cb rev a2 class 04,03,00 hdr 80
(II) PCI: 00:14:0: chip 10de,0269 card 1043,816a rev a3 class 06,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 04:05:0: chip 104c,8023 card 1043,808b rev 00 class 0c,00,10 hdr 00
(II) PCI: 04:08:0: chip 1106,3038 card 1106,3038 rev 61 class 0c,03,00 hdr 80
(II) PCI: 04:08:1: chip 1106,3038 card 1106,3038 rev 61 class 0c,03,00 hdr 80
(II) PCI: 04:08:2: chip 1106,3104 card 1106,3104 rev 63 class 0c,03,20 hdr 80
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfd800000 - 0xfd8fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xfd700000 - 0xfd7fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[1] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[2] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[3] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:4:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xfd900000 - 0xfd9fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:16:0), (0,4,4), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfdb00000 - 0xfdbfffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xfda00000 - 0xfdafffff (0x100000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(0:5:0) nVidia Corporation C51PV [GeForce 6150] rev 162, Mem @ 0xfc000000/24, 0xd0000000/28, 0xfb000000/24
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
	[0] -1	0	0xfdbfe000 - 0xfdbfe0ff (0x100) MX[B]
	[1] -1	0	0xfdbf8000 - 0xfdbfbfff (0x4000) MX[B]
	[2] -1	0	0xfdbff000 - 0xfdbff7ff (0x800) MX[B]
	[3] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[4] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[5] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[6] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[7] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[8] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[9] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[13] -1	0	0x00009c00 - 0x00009c1f (0x20) IX[B]
	[14] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[15] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[16] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[17] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[18] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[19] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[21] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[22] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[23] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[24] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[25] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[26] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[27] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdbfe000 - 0xfdbfe0ff (0x100) MX[B]
	[1] -1	0	0xfdbf8000 - 0xfdbfbfff (0x4000) MX[B]
	[2] -1	0	0xfdbff000 - 0xfdbff7ff (0x800) MX[B]
	[3] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[4] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[5] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[6] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[7] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[8] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[9] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[13] -1	0	0x00009c00 - 0x00009c1f (0x20) IX[B]
	[14] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[15] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[16] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[17] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[18] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[19] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[21] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[22] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[23] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[24] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[25] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[26] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[27] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
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
	[4] -1	0	0xfdbfe000 - 0xfdbfe0ff (0x100) MX[B]
	[5] -1	0	0xfdbf8000 - 0xfdbfbfff (0x4000) MX[B]
	[6] -1	0	0xfdbff000 - 0xfdbff7ff (0x800) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[8] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[9] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[10] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[11] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[12] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[13] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[19] -1	0	0x00009c00 - 0x00009c1f (0x20) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[21] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[22] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[23] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[24] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[25] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[27] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[28] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[29] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[30] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[31] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[32] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[33] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
(II) LoadModule: "i2c"(II) Module already built-in
(II) LoadModule: "ddc"(II) Module already built-in
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9639
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9639
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) NVIDIA dlloader X Driver  1.0-9639  Mon Apr 16 20:20:25 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00:05:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdbfe000 - 0xfdbfe0ff (0x100) MX[B]
	[5] -1	0	0xfdbf8000 - 0xfdbfbfff (0x4000) MX[B]
	[6] -1	0	0xfdbff000 - 0xfdbff7ff (0x800) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[8] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[9] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[10] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[11] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[12] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[13] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[19] -1	0	0x00009c00 - 0x00009c1f (0x20) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[21] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[22] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[23] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[24] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[25] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[27] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[28] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[29] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[30] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[31] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[32] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[33] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdbfe000 - 0xfdbfe0ff (0x100) MX[B]
	[5] -1	0	0xfdbf8000 - 0xfdbfbfff (0x4000) MX[B]
	[6] -1	0	0xfdbff000 - 0xfdbff7ff (0x800) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[8] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[9] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[10] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[11] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[12] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[13] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[22] -1	0	0x00009c00 - 0x00009c1f (0x20) IX[B]
	[23] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[24] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[25] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[26] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[27] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[28] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[30] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[31] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[32] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[33] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[34] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[35] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[36] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6150 at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.22.33.07
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6150 at PCI:0:5:0:
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: TV-0
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "832x624"; removing.
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) NVIDIA(0): Primary V_BIOS segment is: 0xc000
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfdbfe000 - 0xfdbfe0ff (0x100) MX[B]
	[8] -1	0	0xfdbf8000 - 0xfdbfbfff (0x4000) MX[B]
	[9] -1	0	0xfdbff000 - 0xfdbff7ff (0x800) MX[B]
	[10] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[11] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[12] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[13] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[14] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[15] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[16] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[25] -1	0	0x00009c00 - 0x00009c1f (0x20) IX[B]
	[26] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[27] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[28] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[29] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[30] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[31] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[32] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[33] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[34] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[35] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[36] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[37] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[38] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[39] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
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
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x6d) [0x48670d]
1: /lib/libc.so.6 [0x2b9fdd3b47d0]
2: /usr/lib/libGLcore.so.1(_nv000084gl+0) [0x2b9fdeea7360]

Fatal server error:
Caught signal 11.  Server aborting
```

---

### Post by hangfire on 2007-11-19
Looks like it died trying to load OpenGL. Try commenting out anything with "gl" in it, in the Section "Module" portion of ***/etc/X11/xorg.conf*** .

The **Wacom** errors are non-critical.

The  **font path element**  error is non-critical.

If you still can't get anywhere, please post your xorg.conf file. Also tell us what H/W you are running on, especially the video card.

Good luck.
-HF

---

### Post by PaulRSte on 2007-11-20
Hangfire

Thanks for that.  Can't do anything until this evening (UK time).  With you mentioning video card though I google'd "Caught signal 11" and came up with the following link [http://www.linuxquestions.org/questions/debian-26/caught-signal-11.-server-aborting-256896/]("http://www.linuxquestions.org/questions/debian-26/caught-signal-11.-server-aborting-256896/") which says something to the effect that the user had installed the official NVIDIA drivers and the Debian drivers nvidia-glx and after removing the latter it was ok.

Well, I installed the latest NVIDIA driver about a month ago and the gutsy upgrade installed some NVIDIA drivers, presumably the package above.

Question is, which should I remove?  I've seen loads of advice re mythtv to install latest nvidia drivers but this seems to be having an adverse effect when upgrading.

Any advice here would be extremely helpfull.

System, by the way, is an ASUS M2NPV-VM with NVIDIA GeForce 6150 + nForce 430

---

### Post by hangfire on 2007-11-20
To see which drivers you are running (or trying to run), take a look at the Section "Device" portion of your xorg.conf, at the Driver entry in double quotes.

**nv** is the FOSS (free and open source software) drivers, which most get from Xorg.

**nvidia** is the proprietary drivers, from the company's website.

It is highly recommended to revert to the FOSS drivers before doing an Upgrade, and then download the latest and greatest if going back to proprietary drivers.

-HF

---

### Post by PaulRSte on 2007-11-20
Hangfire

System is an Antec Fusion case with an ASUS M2NPV-VM mother board with onboard NVIDIA GEFORCE 6150 and nforce 430, Dual core Athlon 64 and 2GB RAM plus 2 500GB Deskstars and a DVD writer, and a Nova T 500 dual TV tuner card.  RAID 1 is used for the root partition and /home.  It is used for mythtv and so no monitor is attached, only a 28" widescreen TV (CRT).  Prior to upgrading to Gutsy it was running on 64 bit Feisty.  As I had aspect ratio issues with mythtv I had added the additional nvidia features via the restricted driver manager and when this didn't improve matters, had installed the latest drivers from the nvidia site (probably a huge mistake and still didn't improve anything).  I decided to upgrade to Gutsy as I had IR issues and whilst fixable under Feisty, seemed a bit like reinventing the wheel now that Gutsy was live.

This loads fine from the UBUNTU Feisty Fawn Live CD (64 bit) and I can then install mdadm into this to access md0 (/) and md1 (/home) as required.  I am entering this post on the system booted in this mannner but via VNC from a windows XP PC.

I downloaded the Gutsy Live CD 64 bit last night.  When I boot from that then it finishes with a quarter inch line right across the top of the TV and the rest of the screen blank, so it looks as though it is going into the desktop in some manner.

Re my upgraded disks - I have changed the driver from "nvidia" to "nv" and get a similar display  to the live CD.  When I also comment out the glx line in the module line it finishes booting with 3 lines across the top of the TV that wrap slightly to the next line.

xorg.conf posted as requested

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Thu Oct  4 10:48:30 PDT 2007

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
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
#    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation C51PV [GeForce 6150]"
    Driver         "nv"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation C51PV [GeForce 6150]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

---

### Post by PaulRSte on 2007-11-21
After googling around this issue for a couple of days I was starting to think that I was the only one with this problem.  I started checking through xorg.conf again and everything that I had seen in various posts was actually correct.

When I looked at the monitor section it was saying "standard monitor" so I unplugged the tv and connected an svga monitor and rebooted (the M2NPV-VM only allows a TV or an SVGA monitor to be connected, not both)

It worked!  I removed the comment from the glx line in the module section, rebooted again, and it still worked.  I applied the 7 updates that were waiting to be installed and then went into the restricted driver manager and enabled the NVIDIA driver.  I loaded the NVIDIA X Server Settings utility after rebooting and enabled the tv output, unplugged the SVGA and rebooted and the TV now worked again.  Loaded mythtv front end and all working well.

My advice to Mythtv users upgrading from Feisty to Gutsy and using nvidia cards is:-

1) Ensure that your xorg.conf is using the FOSS driver, i.e. that the driver entry in the driver section contains "nv" and NOT "nvidia"

2) Ensure that you have an SVGA monitor plugged and then do the upgrade.

3) After upgrading, perform any updates required and after rebooting if required, enable the TV output in the nvidia x server settings utility and then try the TV output after a reboot.

The annoying thing here is that the system works fine with only the TV connected when booting from the Feisty Live CD.  It doesn't work when booted from the Gutsy Live CD.  This means always needing an SVGA monitor on hand for trouble shooting so is quite an inconvenience for mythtv use.

Thanks to hangfire for taking me through the problem and basically showing me where the problem lay.

---

### Post by hangfire on 2007-11-21
You're welcome! I'm glad you came to a resolution, as I was running out of ideas :)

I've gotten a lot of help here, it's nice to give back.

-HF

---

