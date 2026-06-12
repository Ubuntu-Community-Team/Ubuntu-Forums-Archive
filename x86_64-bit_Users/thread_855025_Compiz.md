---
title: "Compiz"
date: 2008-07-10
forum: x86 64-bit Users
---

### Post by Ducksgoquak on 2008-07-10
Hi guys! I'm a new convert from Windows to Ubuntu and am having a bit of a problem with compiz and general slow performance. I'm running a duo core pentium on a 680i nvidia motherboard and an Nvidia 7800 gt + 2 gigs of ram.

I installed Ubuntu 8.04 64 bit and am having a bit of trouble i can't seem to figure out. 

If i try to enable visual effects i get the error that desktop effects cannot be enabled. I've tried installing my nvidia drivers(using EnvyNG), reinstalling my nvidia drivers, reinstalling compiz, etc. If i do try and use compiz the system locks up and one time i ended up with a black screen with vertical white lines /shrug. 

Edit: I ran compiz desktop again and it lagged my system hard for almost a minute but then came out. It managed to change my visual effects to normal but the only thing that actually appears to have changed are the top of my windows (orange bar) disappears. Changing visual effects back to none fixed that. 

Now i have installed a lot of stuff(possibly something i shouldn't have) but this didn't work even when this was a fresh install. 

I believe my drivers and my video card are both ok but i'm a bit lost on what to do from here.

I installed and used Compiz-Check (took almost 5 minutes to check hardware... possibly something there) but everything checked out ok

```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G70 [GeForce 7800 GT] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

not exactly what other information is needed to help me so here is a bunch of it!

```
lspci |grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)

```

here is the output of my Xorg.0.log file
There are several errors present here but i'm not sure what they mean or how to fix them:( But i'm sure they could have something to do with my problem. 

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) Warning, couldn't open module type1
(WW) NVIDIA(0): WAIT (2, 7, 0x8000, 0x0000fac0, 0x0000f478)
(WW) NVIDIA(0): WAIT (1, 7, 0x8000, 0x0000fac0, 0x0000f478)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x0000fac0, 0x0000f488)
(WW) NVIDIA(0): WAIT (1, 6, 0x8000, 0x0000fac0, 0x0000f488)

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
Current Operating System: Linux Compuper 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul  9 21:51:43 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bd660
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,03a1 card 10de,c55e rev a2 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,03ac card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,03aa card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,03a9 card 10de,c55e rev a1 class 05,00,00 hdr 00
(II) PCI: 00:00:4: chip 10de,03ab card 10de,c55e rev a1 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,03a8 card 10de,c55e rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,03b5 card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,03b4 card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,03ad card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:1: chip 10de,03ae card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:2: chip 10de,03af card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:3: chip 10de,03b0 card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:4: chip 10de,03b1 card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:5: chip 10de,03b2 card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:6: chip 10de,03b3 card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,03b6 card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:02:1: chip 10de,03bc card 10de,c55e rev a1 class 05,00,00 hdr 00
(II) PCI: 00:02:2: chip 10de,03ba card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:03:0: chip 10de,03b7 card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0369 card 10de,c55e rev a1 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0360 card 10de,c55e rev a2 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0368 card 10de,c55e rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,036c card 10de,c55e rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,036d card 10de,c55e rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,036e card f0de,c55e rev a1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,037f card 10de,c55e rev a2 class 01,01,85 hdr 80
(II) PCI: 00:0e:1: chip 10de,037f card 10de,c55e rev a2 class 01,01,85 hdr 80
(II) PCI: 00:0e:2: chip 10de,037f card 10de,c55e rev a2 class 01,01,85 hdr 80
(II) PCI: 00:0f:0: chip 10de,0370 card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:0f:1: chip 10de,0371 card 10de,c55e rev a2 class 04,03,00 hdr 80
(II) PCI: 00:11:0: chip 10de,0373 card 10de,c55e rev a2 class 06,80,00 hdr 00
(II) PCI: 00:12:0: chip 10de,0373 card 10de,c55e rev a2 class 06,80,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0092 card 10de,0301 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:07:0: chip 104c,8023 card 10de,c55e rev 00 class 0c,00,10 hdr 00
(II) PCI: 02:0a:0: chip 168c,0013 card 1186,3a13 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:3:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xcc000000 - 0xceffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:15:0), (0,2,2), BCTRL: 0x0a04 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xcfe00000 - 0xcfefffff (0x100000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation G70 [GeForce 7800 GT] rev 161, Mem @ 0xcc000000/24, 0xb0000000/28, 0xcd000000/24, I/O @ 0x9c00/7
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
	[0] -1	0	0xcfee0000 - 0xcfeeffff (0x10000) MX[B]
	[1] -1	0	0xcfef8000 - 0xcfefbfff (0x4000) MX[B]
	[2] -1	0	0xcfeff000 - 0xcfeff7ff (0x800) MX[B]
	[3] -1	0	0xcfff5000 - 0xcfff500f (0x10) MX[B]
	[4] -1	0	0xcfff6000 - 0xcfff60ff (0x100) MX[B]
	[5] -1	0	0xcfff7000 - 0xcfff7fff (0x1000) MX[B]
	[6] -1	0	0xcfff8000 - 0xcfff800f (0x10) MX[B]
	[7] -1	0	0xcfff9000 - 0xcfff90ff (0x100) MX[B]
	[8] -1	0	0xcfffa000 - 0xcfffafff (0x1000) MX[B]
	[9] -1	0	0xcfff0000 - 0xcfff3fff (0x4000) MX[B]
	[10] -1	0	0xcfffb000 - 0xcfffbfff (0x1000) MX[B]
	[11] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[12] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[13] -1	0	0xcfffe000 - 0xcfffe0ff (0x100) MX[B]
	[14] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[15] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[16] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[18] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[19] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b00f (0x10) IX[B]
	[21] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[23] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[25] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[26] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[27] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[28] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[29] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[31] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[32] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[33] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[34] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[35] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[36] -1	0	0x0000f000 - 0x0000f03f (0x40) IX[B]
	[37] -1	0	0x0000f400 - 0x0000f43f (0x40) IX[B]
	[38] -1	0	0x0000f800 - 0x0000f83f (0x40) IX[B]
	[39] -1	0	0x0000fc00 - 0x0000fc7f (0x80) IX[B]
	[40] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xcfee0000 - 0xcfeeffff (0x10000) MX[B]
	[1] -1	0	0xcfef8000 - 0xcfefbfff (0x4000) MX[B]
	[2] -1	0	0xcfeff000 - 0xcfeff7ff (0x800) MX[B]
	[3] -1	0	0xcfff5000 - 0xcfff500f (0x10) MX[B]
	[4] -1	0	0xcfff6000 - 0xcfff60ff (0x100) MX[B]
	[5] -1	0	0xcfff7000 - 0xcfff7fff (0x1000) MX[B]
	[6] -1	0	0xcfff8000 - 0xcfff800f (0x10) MX[B]
	[7] -1	0	0xcfff9000 - 0xcfff90ff (0x100) MX[B]
	[8] -1	0	0xcfffa000 - 0xcfffafff (0x1000) MX[B]
	[9] -1	0	0xcfff0000 - 0xcfff3fff (0x4000) MX[B]
	[10] -1	0	0xcfffb000 - 0xcfffbfff (0x1000) MX[B]
	[11] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[12] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[13] -1	0	0xcfffe000 - 0xcfffe0ff (0x100) MX[B]
	[14] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[15] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[16] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[18] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[19] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b00f (0x10) IX[B]
	[21] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[23] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[25] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[26] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[27] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[28] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[29] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[31] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[32] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[33] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[34] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[35] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[36] -1	0	0x0000f000 - 0x0000f03f (0x40) IX[B]
	[37] -1	0	0x0000f400 - 0x0000f43f (0x40) IX[B]
	[38] -1	0	0x0000f800 - 0x0000f83f (0x40) IX[B]
	[39] -1	0	0x0000fc00 - 0x0000fc7f (0x80) IX[B]
	[40] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
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
	[4] -1	0	0xcfee0000 - 0xcfeeffff (0x10000) MX[B]
	[5] -1	0	0xcfef8000 - 0xcfefbfff (0x4000) MX[B]
	[6] -1	0	0xcfeff000 - 0xcfeff7ff (0x800) MX[B]
	[7] -1	0	0xcfff5000 - 0xcfff500f (0x10) MX[B]
	[8] -1	0	0xcfff6000 - 0xcfff60ff (0x100) MX[B]
	[9] -1	0	0xcfff7000 - 0xcfff7fff (0x1000) MX[B]
	[10] -1	0	0xcfff8000 - 0xcfff800f (0x10) MX[B]
	[11] -1	0	0xcfff9000 - 0xcfff90ff (0x100) MX[B]
	[12] -1	0	0xcfffa000 - 0xcfffafff (0x1000) MX[B]
	[13] -1	0	0xcfff0000 - 0xcfff3fff (0x4000) MX[B]
	[14] -1	0	0xcfffb000 - 0xcfffbfff (0x1000) MX[B]
	[15] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[16] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[17] -1	0	0xcfffe000 - 0xcfffe0ff (0x100) MX[B]
	[18] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[19] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[20] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[21] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[25] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[26] -1	0	0x0000b000 - 0x0000b00f (0x10) IX[B]
	[27] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[28] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[29] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[30] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[31] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[32] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[33] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[34] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[35] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[36] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[37] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[38] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[39] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[40] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[41] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[42] -1	0	0x0000f000 - 0x0000f03f (0x40) IX[B]
	[43] -1	0	0x0000f400 - 0x0000f43f (0x40) IX[B]
	[44] -1	0	0x0000f800 - 0x0000f83f (0x40) IX[B]
	[45] -1	0	0x0000fc00 - 0x0000fc7f (0x80) IX[B]
	[46] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  173.14.05  Mon May 19 00:27:33 PDT 2008
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) NVIDIA dlloader X Driver  173.14.05  Mon May 19 00:09:56 PDT 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcfee0000 - 0xcfeeffff (0x10000) MX[B]
	[5] -1	0	0xcfef8000 - 0xcfefbfff (0x4000) MX[B]
	[6] -1	0	0xcfeff000 - 0xcfeff7ff (0x800) MX[B]
	[7] -1	0	0xcfff5000 - 0xcfff500f (0x10) MX[B]
	[8] -1	0	0xcfff6000 - 0xcfff60ff (0x100) MX[B]
	[9] -1	0	0xcfff7000 - 0xcfff7fff (0x1000) MX[B]
	[10] -1	0	0xcfff8000 - 0xcfff800f (0x10) MX[B]
	[11] -1	0	0xcfff9000 - 0xcfff90ff (0x100) MX[B]
	[12] -1	0	0xcfffa000 - 0xcfffafff (0x1000) MX[B]
	[13] -1	0	0xcfff0000 - 0xcfff3fff (0x4000) MX[B]
	[14] -1	0	0xcfffb000 - 0xcfffbfff (0x1000) MX[B]
	[15] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[16] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[17] -1	0	0xcfffe000 - 0xcfffe0ff (0x100) MX[B]
	[18] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[19] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[20] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[21] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[25] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[26] -1	0	0x0000b000 - 0x0000b00f (0x10) IX[B]
	[27] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[28] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[29] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[30] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[31] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[32] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[33] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[34] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[35] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[36] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[37] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[38] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[39] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[40] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[41] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[42] -1	0	0x0000f000 - 0x0000f03f (0x40) IX[B]
	[43] -1	0	0x0000f400 - 0x0000f43f (0x40) IX[B]
	[44] -1	0	0x0000f800 - 0x0000f83f (0x40) IX[B]
	[45] -1	0	0x0000fc00 - 0x0000fc7f (0x80) IX[B]
	[46] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcfee0000 - 0xcfeeffff (0x10000) MX[B]
	[5] -1	0	0xcfef8000 - 0xcfefbfff (0x4000) MX[B]
	[6] -1	0	0xcfeff000 - 0xcfeff7ff (0x800) MX[B]
	[7] -1	0	0xcfff5000 - 0xcfff500f (0x10) MX[B]
	[8] -1	0	0xcfff6000 - 0xcfff60ff (0x100) MX[B]
	[9] -1	0	0xcfff7000 - 0xcfff7fff (0x1000) MX[B]
	[10] -1	0	0xcfff8000 - 0xcfff800f (0x10) MX[B]
	[11] -1	0	0xcfff9000 - 0xcfff90ff (0x100) MX[B]
	[12] -1	0	0xcfffa000 - 0xcfffafff (0x1000) MX[B]
	[13] -1	0	0xcfff0000 - 0xcfff3fff (0x4000) MX[B]
	[14] -1	0	0xcfffb000 - 0xcfffbfff (0x1000) MX[B]
	[15] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[16] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[17] -1	0	0xcfffe000 - 0xcfffe0ff (0x100) MX[B]
	[18] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[19] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[20] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[21] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[28] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[29] -1	0	0x0000b000 - 0x0000b00f (0x10) IX[B]
	[30] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[31] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[32] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[33] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[34] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[35] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[36] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[37] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[38] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[39] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[40] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[41] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[42] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[43] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[44] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[45] -1	0	0x0000f000 - 0x0000f03f (0x40) IX[B]
	[46] -1	0	0x0000f400 - 0x0000f43f (0x40) IX[B]
	[47] -1	0	0x0000f800 - 0x0000f83f (0x40) IX[B]
	[48] -1	0	0x0000fc00 - 0x0000fc7f (0x80) IX[B]
	[49] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
	[50] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[51] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7800 GT (G70) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.70.02.13.01
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7800 GT at PCI:1:0:0:
(--) NVIDIA(0):     Acer AL1914 (CRT-0)
(--) NVIDIA(0): Acer AL1914 (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (87, 86); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcfee0000 - 0xcfeeffff (0x10000) MX[B]
	[5] -1	0	0xcfef8000 - 0xcfefbfff (0x4000) MX[B]
	[6] -1	0	0xcfeff000 - 0xcfeff7ff (0x800) MX[B]
	[7] -1	0	0xcfff5000 - 0xcfff500f (0x10) MX[B]
	[8] -1	0	0xcfff6000 - 0xcfff60ff (0x100) MX[B]
	[9] -1	0	0xcfff7000 - 0xcfff7fff (0x1000) MX[B]
	[10] -1	0	0xcfff8000 - 0xcfff800f (0x10) MX[B]
	[11] -1	0	0xcfff9000 - 0xcfff90ff (0x100) MX[B]
	[12] -1	0	0xcfffa000 - 0xcfffafff (0x1000) MX[B]
	[13] -1	0	0xcfff0000 - 0xcfff3fff (0x4000) MX[B]
	[14] -1	0	0xcfffb000 - 0xcfffbfff (0x1000) MX[B]
	[15] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[16] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[17] -1	0	0xcfffe000 - 0xcfffe0ff (0x100) MX[B]
	[18] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[19] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[20] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[21] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[28] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[29] -1	0	0x0000b000 - 0x0000b00f (0x10) IX[B]
	[30] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[31] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[32] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[33] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[34] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[35] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[36] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[37] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[38] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[39] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[40] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[41] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[42] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[43] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[44] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[45] -1	0	0x0000f000 - 0x0000f03f (0x40) IX[B]
	[46] -1	0	0x0000f400 - 0x0000f43f (0x40) IX[B]
	[47] -1	0	0x0000f800 - 0x0000f83f (0x40) IX[B]
	[48] -1	0	0x0000fc00 - 0x0000fc7f (0x80) IX[B]
	[49] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
	[50] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[51] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
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
(**) Keyboard0: always reports core events
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/psaux"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: always reports core events
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(**) Mouse0: Sensitivity: 1
(II) evaluating device (Mouse0)
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) evaluating device (Keyboard0)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
(WW) NVIDIA(0): WAIT (2, 7, 0x8000, 0x0000fac0, 0x0000f478)
(WW) NVIDIA(0): WAIT (1, 7, 0x8000, 0x0000fac0, 0x0000f478)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x0000fac0, 0x0000f488)
(WW) NVIDIA(0): WAIT (1, 6, 0x8000, 0x0000fac0, 0x0000f488)
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
SetGrabKeysState - disabled
SetGrabKeysState - enabled
```

Thanks in advance!

---

### Post by kid-lj on 2008-07-10
I don't know,but I don't think you should run the 64 bit os.
Maybe 32 bit better.Anyway,I am a newbie too.

---

### Post by Ducksgoquak on 2008-07-10
Eh i kind of want to get 64 bit working:) I like a bit of a challenge, just need to be prodded in the right direction! Only my second day of linux so im definitely a newb!

---

### Post by darkknight045 on 2008-07-10
If I recall correctly, your video card could be the issue.  I've heard that for some reason the 7800 cards don't seem to work well in Ubuntu.  Can't be sure though, I run the 7950GT(and the 8600 GM on my laptop) so this is strictly second hand information.

---

### Post by stchman on 2008-07-10
All you need to do is enable the restricted driver for that card.  I have a 7600GT and it works perfectly with Compiz under 64 bit Hardy.

---

### Post by Ducksgoquak on 2008-07-10
Hmmmmmm... My graphics card isn't listed in the hardware drivers window... How do i add it there? I'm not sure where the heck it went:( 

This is most likely my problem though:)

EDIT: I figured it out, just had to reinstall the restricted software package. I have no idea how my video card went missing from that list.

---

