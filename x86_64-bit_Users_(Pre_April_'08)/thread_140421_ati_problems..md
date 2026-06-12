---
title: "ati problems."
date: 2006-03-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sommer on 2006-03-06
I have followed the guide for ati-installing. I have installed all the
*.deb files on my system with "dpkg -i"

I have updated my kernel, but I cant run the aticonfig-command or
fglxconfig (if it should exist)

After rebooting my system cant start X (Gnome).

I tryed to run the

 sudo dpkg-reconfigure xserver-xorg and set it to vesa, but still it make
and error.. so now after trying to install ati, nothing works.. my god..!!!

Here is my log, sry it is very ugly, because i copy/pasted it from windows:
nb: My computer is a 

[http://search.hp.com/query.html?charset=iso-8859-1&hpvc=sitewide&la=en&qs=&lk=1&rf=0&uf=1&nh=10&st=1&qt=HP+Pavilion+zv6000+Notebook+PC&ocoldqt=zv6000&oc=453300](http://search.hp.com/query.html?charset=iso-8859-1&hpvc=sitewide&la=en&qs=&lk=1&rf=0&uf=1&nh=10&st=1&qt=HP+Pavilion+zv6000+Notebook+PC&ocoldqt=zv6000&oc=453300)

with an "ATI Xpress Radeon 200M" grafikcard.



************************log*****************************



X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux PornstarLinux 2.6.12-10-386 #1 Mon Feb 13 12:13:15 UTC 2006 i686
Build Date: 10 October 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Feb 13 12:13:15 UTC 2006 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar  6 03:24:56 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Standard Skærm"
(**) |   |-->Device "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
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
(II) PCI: 00:00:0: chip 1002,5950 card 103c,3085 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,5a3f card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 1002,5a36 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:13:0: chip 1002,4374 card 1002,4374 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 1002,4375 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 1002,4373 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 103c,3085 rev 10 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 103c,3085 rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 0000,0000 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:14:5: chip 1002,4370 card 103c,3085 rev 01 class 04,01,00 hdr 80
(II) PCI: 00:14:6: chip 1002,4378 card 103c,3085 rev 01 class 07,03,00 hdr 80
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:05:0: chip 1002,5955 card 103c,3085 rev 00 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 104c,8023 card 103c,3085 rev 00 class 0c,00,10 hdr 00
(II) PCI: 03:02:0: chip 14e4,4320 card 103c,12fa rev 03 class 02,80,00 hdr 00
(II) PCI: 03:04:0: chip 104c,8031 card 4000,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 03:04:3: chip 104c,8033 card 103c,3085 rev 00 class 01,80,00 hdr 80
(II) PCI: 03:04:4: chip 104c,8034 card 103c,3085 rev 00 class 08,05,00 hdr 80
(II) PCI: 03:06:0: chip 10ec,8139 card 103c,3085 rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xb0100000 - 0xb01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:4:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:20:4), (0,3,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xb0200000 - 0xb02fffff (0x100000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:0), (-1,-1,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:1), (-1,-1,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:2), (-1,-1,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:3), (-1,-1,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 4: bridge is at (3:4:0), (3,4,7), BCTRL: 0x05c0 (VGA_EN is cleared)
(--) PCI:*(1:5:0) ATI Technologies Inc unknown chipset (0x5955) rev 0, Mem @ 0xc0000000/28, 0xb0100000/16, I/O @ 0x9000/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xb020a400 - 0xb020a4ff (0x100) MX[B]
	[1] -1	0	0xb0208800 - 0xb02088ff (0x100) MX[B]
	[2] -1	0	0xb0208c00 - 0xb0208cff (0x100) MX[B]
	[3] -1	0	0xb020a000 - 0xb020a0ff (0x100) MX[B]
	[4] -1	0	0xb0206000 - 0xb0207fff (0x2000) MX[B]
	[5] -1	0	0xb0204000 - 0xb0205fff (0x2000) MX[B]
	[6] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[7] -1	0	0xb0208000 - 0xb02087ff (0x800) MX[B]
	[8] -1	0	0xb0003800 - 0xb00038ff (0x100) MX[B]
	[9] -1	0	0xb0003400 - 0xb00034ff (0x100) MX[B]
	[10] -1	0	0xb0003000 - 0xb00033ff (0x400) MX[B]
	[11] -1	0	0xb0002000 - 0xb0002fff (0x1000) MX[B]
	[12] -1	0	0xb0001000 - 0xb0001fff (0x1000) MX[B]
	[13] -1	0	0xb0000000 - 0xb0000fff (0x1000) MX[B]
	[14] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[23] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xb020a400 - 0xb020a4ff (0x100) MX[B]
	[1] -1	0	0xb0208800 - 0xb02088ff (0x100) MX[B]
	[2] -1	0	0xb0208c00 - 0xb0208cff (0x100) MX[B]
	[3] -1	0	0xb020a000 - 0xb020a0ff (0x100) MX[B]
	[4] -1	0	0xb0206000 - 0xb0207fff (0x2000) MX[B]
	[5] -1	0	0xb0204000 - 0xb0205fff (0x2000) MX[B]
	[6] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[7] -1	0	0xb0208000 - 0xb02087ff (0x800) MX[B]
	[8] -1	0	0xb0003800 - 0xb00038ff (0x100) MX[B]
	[9] -1	0	0xb0003400 - 0xb00034ff (0x100) MX[B]
	[10] -1	0	0xb0003000 - 0xb00033ff (0x400) MX[B]
	[11] -1	0	0xb0002000 - 0xb0002fff (0x1000) MX[B]
	[12] -1	0	0xb0001000 - 0xb0001fff (0x1000) MX[B]
	[13] -1	0	0xb0000000 - 0xb0000fff (0x1000) MX[B]
	[14] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[23] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
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
	[5] -1	0	0xb020a400 - 0xb020a4ff (0x100) MX[B]
	[6] -1	0	0xb0208800 - 0xb02088ff (0x100) MX[B]
	[7] -1	0	0xb0208c00 - 0xb0208cff (0x100) MX[B]
	[8] -1	0	0xb020a000 - 0xb020a0ff (0x100) MX[B]
	[9] -1	0	0xb0206000 - 0xb0207fff (0x2000) MX[B]
	[10] -1	0	0xb0204000 - 0xb0205fff (0x2000) MX[B]
	[11] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[12] -1	0	0xb0208000 - 0xb02087ff (0x800) MX[B]
	[13] -1	0	0xb0003800 - 0xb00038ff (0x100) MX[B]
	[14] -1	0	0xb0003400 - 0xb00034ff (0x100) MX[B]
	[15] -1	0	0xb0003000 - 0xb00033ff (0x400) MX[B]
	[16] -1	0	0xb0002000 - 0xb0002fff (0x1000) MX[B]
	[17] -1	0	0xb0001000 - 0xb0001fff (0x1000) MX[B]
	[18] -1	0	0xb0000000 - 0xb0000fff (0x1000) MX[B]
	[19] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[20] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[24] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[25] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[26] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[27] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[30] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(WW) Ignoring request to load module GLcore
(II) LoadModule: "bitmap"
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

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Fatal server error:
Caught signal 11.  Server aborting


Please consult the The X.Org Foundation support 
	 at [http://wiki.X.Org](http://wiki.X.Org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

---

### Post by Sommer on 2006-03-06
oh, and I downgraded the libdri.a - file

---

### Post by gabi_2 on 2006-03-06
Hi !

I don't know is this helps or not but any way. Have you try to modify the xorg.conf file?. Try to add Device part 
Option "NoAccel" "True" and reboot. This way I got the X running !

---

