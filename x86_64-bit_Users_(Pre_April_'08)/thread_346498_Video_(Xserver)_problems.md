---
title: "Video (Xserver) problems"
date: 2007-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Shelnutt2 on 2007-01-25
Everything was working fine and Tuesday morning I rebooted into windows to print some stuff, I restart went to load ubuntu and bam, no video at the xserver. When xserver starts, no video. I booted into recovery mode and it worked fine, started xserver and no video. I didn't change anything, all I did was reboot. All I get is a blank/black screen, no error messages, nothing. I though this might have been a libc6 error, but I've update my package and have the latest version of libc6, so thats not it. I've made a post on ocforums and they are stumped. I've also attached my log files in that thread ([link]("http://www.ocforums.com/showthread.php?t=497225")).

I'm running Edgy (64 bit). System specs are in my sig.

Thanks for the help.

---

### Post by incubus on 2007-01-25
I did check your log files, but I fail to see the source of the problem.

Somebody mentioned the "libc6" problem, you're sure you have the corrected version running?

Can you post your Xorg.conf file as well?

incubus

---

### Post by Shelnutt2 on 2007-01-26
I changed my driver to ati and now I get the error message "(EE) No devices detected."

Xserver log:
```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 x86_64 
Current Operating System: Linux Ubuntu64-D 2.6.17-10-generic #2 SMP Tue Dec 5 21:16:35 UTC 2006 x86_64
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 26 05:53:45 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Samsung 940bw"
(**) |   |-->Device "ATI RADEON X1650 Pro"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(--) using VT number 2

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,29a0 card 1043,81ea rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,29a1 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1a:0: chip 8086,2834 card 1043,81ec rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1043,81ec rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1043,81ec rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2847 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:5: chip 8086,2849 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1043,81ec rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1043,81ec rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1043,81ec rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1043,81ec rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev f2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2810 card 1043,81ec rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2820 card 1043,81ec rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 1043,81ec rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2825 card 1043,81ec rev 02 class 01,01,85 hdr 00
(II) PCI: 01:00:0: chip 1002,71c6 card 17af,2058 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,71e6 card 17af,2059 rev 00 class 03,80,00 hdr 00
(II) PCI: 02:00:0: chip 11ab,4364 card 1148,4340 rev 12 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 197b,2363 card 1043,81e4 rev 02 class 01,06,01 hdr 80
(II) PCI: 03:00:1: chip 197b,2363 card 1043,81e4 rev 02 class 01,01,85 hdr 00
(II) PCI: 05:02:0: chip 1102,0008 card 1102,1001 rev 00 class 04,01,00 hdr 00
(II) PCI: 05:03:0: chip 104c,8023 card 1043,815b rev 00 class 0c,00,10 hdr 00
(II) PCI: 05:04:0: chip 11ab,4320 card 1043,811a rev 14 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00006000 - 0x00008fff (0x3000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xff600000 - 0xff6fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbfe00000 - 0xdfdfffff (0x20000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:4), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xff800000 - 0xff8fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:5), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00009000 - 0x00009fff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xff700000 - 0xff7fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xff900000 - 0xff9fffff (0x100000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x500fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x71c6) rev 0, Mem @ 0xc0000000/28, 0xff6f0000/16, I/O @ 0x8000/8, BIOS @ 0xff6c0000/17
(--) PCI: (1:0:1) ATI Technologies Inc unknown chipset (0x71e6) rev 0, Mem @ 0xff6e0000/16
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
	[0] -1	0	0xff9f4000 - 0xff9f7fff (0x4000) MX[B]
	[1] -1	0	0xff9f8000 - 0xff9fbfff (0x4000) MX[B]
	[2] -1	0	0xff9ff800 - 0xff9fffff (0x800) MX[B]
	[3] -1	0	0xff8fe000 - 0xff8fffff (0x2000) MX[B]
	[4] -1	0	0xff7fc000 - 0xff7fffff (0x4000) MX[B]
	[5] -1	0	0xffaff800 - 0xffaffbff (0x400) MX[B]
	[6] -1	0	0xffaffc00 - 0xffafffff (0x400) MX[B]
	[7] -1	0	0xff6e0000 - 0xff6effff (0x10000) MX[B](B)
	[8] -1	0	0xff6c0000 - 0xff6dffff (0x20000) MX[B](B)
	[9] -1	0	0xff6f0000 - 0xff6fffff (0x10000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[12] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[13] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[14] -1	0	0x0000a480 - 0x0000a483 (0x4) IX[B]
	[15] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[16] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[17] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[18] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[20] -1	0	0x0000c880 - 0x0000c88f (0x10) IX[B]
	[21] -1	0	0x0000cc00 - 0x0000cc03 (0x4) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[23] -1	0	0x0000d080 - 0x0000d083 (0x4) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[25] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[26] -1	0	0x0000e080 - 0x0000e08f (0x10) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[28] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[30] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[31] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[32] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[33] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[34] -1	0	0x0000d480 - 0x0000d49f (0x20) IX[B]
	[35] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[37] -1	0	0x00008000 - 0x000080ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0x50100000 - 0x501000ff (0x100) MX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xff9f4000 - 0xff9f7fff (0x4000) MX[B]
	[1] -1	0	0xff9f8000 - 0xff9fbfff (0x4000) MX[B]
	[2] -1	0	0xff9ff800 - 0xff9fffff (0x800) MX[B]
	[3] -1	0	0xff8fe000 - 0xff8fffff (0x2000) MX[B]
	[4] -1	0	0xff7fc000 - 0xff7fffff (0x4000) MX[B]
	[5] -1	0	0xffaff800 - 0xffaffbff (0x400) MX[B]
	[6] -1	0	0xffaffc00 - 0xffafffff (0x400) MX[B]
	[7] -1	0	0xff6e0000 - 0xff6effff (0x10000) MX[B](B)
	[8] -1	0	0xff6c0000 - 0xff6dffff (0x20000) MX[B](B)
	[9] -1	0	0xff6f0000 - 0xff6fffff (0x10000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[12] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[13] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[14] -1	0	0x0000a480 - 0x0000a483 (0x4) IX[B]
	[15] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[16] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[17] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[18] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[20] -1	0	0x0000c880 - 0x0000c88f (0x10) IX[B]
	[21] -1	0	0x0000cc00 - 0x0000cc03 (0x4) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[23] -1	0	0x0000d080 - 0x0000d083 (0x4) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[25] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[26] -1	0	0x0000e080 - 0x0000e08f (0x10) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[28] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[30] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[31] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[32] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[33] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[34] -1	0	0x0000d480 - 0x0000d49f (0x20) IX[B]
	[35] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[37] -1	0	0x00008000 - 0x000080ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x50100000 - 0x501000ff (0x100) MX[B]
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
	[4] -1	0	0xff9f4000 - 0xff9f7fff (0x4000) MX[B]
	[5] -1	0	0xff9f8000 - 0xff9fbfff (0x4000) MX[B]
	[6] -1	0	0xff9ff800 - 0xff9fffff (0x800) MX[B]
	[7] -1	0	0xff8fe000 - 0xff8fffff (0x2000) MX[B]
	[8] -1	0	0xff7fc000 - 0xff7fffff (0x4000) MX[B]
	[9] -1	0	0xffaff800 - 0xffaffbff (0x400) MX[B]
	[10] -1	0	0xffaffc00 - 0xffafffff (0x400) MX[B]
	[11] -1	0	0xff6e0000 - 0xff6effff (0x10000) MX[B](B)
	[12] -1	0	0xff6c0000 - 0xff6dffff (0x20000) MX[B](B)
	[13] -1	0	0xff6f0000 - 0xff6fffff (0x10000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0x50100000 - 0x501000ff (0x100) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[19] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[20] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[21] -1	0	0x0000a480 - 0x0000a483 (0x4) IX[B]
	[22] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[23] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[24] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[25] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[26] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[27] -1	0	0x0000c880 - 0x0000c88f (0x10) IX[B]
	[28] -1	0	0x0000cc00 - 0x0000cc03 (0x4) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[30] -1	0	0x0000d080 - 0x0000d083 (0x4) IX[B]
	[31] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[32] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[33] -1	0	0x0000e080 - 0x0000e08f (0x10) IX[B]
	[34] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[35] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[36] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[37] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[38] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[39] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[40] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[41] -1	0	0x0000d480 - 0x0000d49f (0x20) IX[B]
	[42] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[43] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[44] -1	0	0x00008000 - 0x000080ff (0x100) IX[B](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 6.6.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) ATI: ATI driver (version 6.6.2) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (AGP?), ATI Rage 128 Pro GL PB (AGP?),
	ATI Rage 128 Pro GL PC (AGP?), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (AGP?), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (AGP?), ATI Rage 128 Pro VR PH (AGP?),
	ATI Rage 128 Pro VR PI (AGP?), ATI Rage 128 Pro VR PJ (AGP?),
	ATI Rage 128 Pro VR PK (AGP?), ATI Rage 128 Pro VR PL (AGP?),
	ATI Rage 128 Pro VR PM (AGP?), ATI Rage 128 Pro VR PN (AGP?),
	ATI Rage 128 Pro VR PO (AGP?), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (AGP?), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (AGP?), ATI Rage 128 Pro VR PT (AGP?),
	ATI Rage 128 Pro VR PU (AGP?), ATI Rage 128 Pro VR PV (AGP?),
	ATI Rage 128 Pro VR PW (AGP?), ATI Rage 128 Pro VR PX (AGP?),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (AGP?),
	ATI Rage 128 4X SF (AGP?), ATI Rage 128 4X SG (AGP?),
	ATI Rage 128 4X SH (AGP?), ATI Rage 128 4X SK (AGP?),
	ATI Rage 128 4X SL (AGP?), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (AGP?), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "ATI RADEON X1650 Pro".
(WW) ATI:  PCI Mach64 in slot 1:0:0 could not be detected!
(WW) ATI:  PCI Mach64 in slot 1:0:1 could not be detected!
(EE) No devices detected.

Fatal server error:
no screens found

```





xserver config:
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
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI RADEON X1650 Pro"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Samsung 940bw"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON X1650 Pro"
	Monitor		"Samsung 940bw"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768" "800x600" "640x480"
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

---

### Post by DrMega on 2007-01-27
Have you tried the propriety ATI driver?

---

### Post by bender5788 on 2007-01-28
Had similar issues when i first setup behind a KVM switch (not that you necessarily are behind one) so i ran this command 
```
sudo dpkg-reconfigure xserver-xorg
``` and make sure you select take your time and select the correct drivers and what not. Not sure if it will help but you will on the other hand then be able to rule that issue out.

---

### Post by bender5788 on 2007-01-28
Ok if the specs in your sig are that of the hardware in question i am just pointing out that your card model is not supported by the looks of it. According to the log you have posted it isn't listed so is most likely not supported or at least that would be my guess but then i'm sure there are some people in here with far more expertise than my self. I'm a techie but yeah programming/linux are not specialty areas yet. (im working on it)

---

### Post by ukripper on 2007-01-28
Try sudo dpkg-reconfigure xserver-xorg at terminal window after putting ur username and password and then reconfigure your X11 then reboot ALT+CTRL+DEL ( I think your PCI bus is causing problem) try above. Hope it works for you.


Ash

---

### Post by Shelnutt2 on 2007-01-28
ok, well with vesa drivers I can startx, but with fglrx I get the black screen. I've purged and reinstalled the fglrx drivers twice. One from apt-get and once I downloaded the installer right from ati's site. I've reconfigured many times with no luck. I ran lspci and from that it looks as if my pci port/bus is set correctly.

---

### Post by Shelnutt2 on 2007-01-31
anyone?

---

### Post by bender5788 on 2007-02-01
Does anyone even know if the card in question is even supported because i can't see it in your log you have pasted up for us.

---

### Post by Shelnutt2 on 2007-02-01
> **bender5788 said:**
> Does anyone even know if the card in question is even supported because i can't see it in your log you have pasted up for us.

Actually, it not. I was reading the documentation for the "ATI" driver and it supports only up to the X850 series. It doesn't support the X1000 series cards. I'm currently using the vesa drivers but tis barely usable as the lag in video is horrible. I really would liek to get the fglrx drivers working again.

I tried to reinstall Ubuntu this morning but wouldn't you know I couldn't get the livecd to work right? Can you guess the problem? Thats right it wouldn't give me video!

I know my video card is fine as I'm sitting in Windows right now, and I've been playing Far Cry.

---

### Post by bender5788 on 2007-02-02
Perhaps its not the driver. Just a question but have you by any chance done a firmware upgrade in windows at all? As when i did one for my 7600 it caused all sorts of issues so i reverted back to the older firmware. Just a thought i'm probably way off the mark here so don't blame me if i'm wrong.

---

### Post by Shelnutt2 on 2007-02-02
> **bender5788 said:**
> Perhaps its not the driver. Just a question but have you by any chance done a firmware upgrade in windows at all? As when i did one for my 7600 it caused all sorts of issues so i reverted back to the older firmware. Just a thought i'm probably way off the mark here so don't blame me if i'm wrong.

I haven't upgraded the firmware. Although I wonder if I should? I appreciate the advice though, I think I'm going to install debian thought and see if that fixes my issue.

---

