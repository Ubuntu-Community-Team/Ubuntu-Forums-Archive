---
title: "I cant install NVIDIA drivers!"
date: 2006-07-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by songochain on 2006-07-09
Hi! i'm back to nvidia since long time and i cant install nvidia official drivers. I've followed method 2 of this how to: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper) Also, i've used a script: envy_8762_64, and i get always same problem:

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15-ubuntu1 x86_64
Current Operating System: Linux ximian 2.6.15-25-amd64-k8 #1 SMP PREEMPT Wed Jun 14 11:39:18 UTC 2006 x86_64
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul  9 14:49:59 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Monitor genérico"
(**) |   |-->Device "NVIDIA Corporation NV43 [GeForce 6600 GT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,005e card 147b,1c1a rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 147b,1c1a rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 147b,1c1a rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 147b,1c1a rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 147b,1c1a rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0059 card 147b,1c1a rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,0053 card 147b,1c1a rev f2 class 01,01,8a hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0a:0: chip 10de,0057 card 147b,1c1a rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:06:0: chip 109e,0350 card 0000,0000 rev 12 class 04,00,00 hdr 00
(II) PCI: 01:08:0: chip 1102,0005 card 1102,0021 rev 00 class 04,01,00 hdr 00
(II) PCI: 05:00:0: chip 10de,0140 card 0000,0000 rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:9:0), (0,1,1), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf4000000 - 0xfbffffff (0x8000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xfdf00000 - 0xfdffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:11:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xfdb00000 - 0xfdbfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:13:0), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfda00000 - 0xfdafffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xfd900000 - 0xfd9fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:14:0), (0,5,5), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 5 I/O range:
	[0] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[1] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[2] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[3] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xd4000000 - 0xdbffffff (0x8000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI: (1:6:0) Brooktree Corporation Bt848 Video Capture rev 18, Mem @ 0xfdfff000/12
(--) PCI:*(5:0:0) nVidia Corporation NV43 [GeForce 6600 GT] rev 162, Mem @ 0xd4000000/26, 0xc8000000/27, 0xda000000/24
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
	[0] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B]
	[1] -1	0	0xfbe00000 - 0xfbffffff (0x200000) MX[B]
	[2] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[3] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[4] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[5] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[6] -1	0	0xda000000 - 0xdaffffff (0x1000000) MX[B](B)
	[7] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[9] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B](B)
	[10] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[13] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[14] -1	0	0x0000f000 - 0x0000f0ff (0x100) IX[B]
	[15] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[16] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[17] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B]
	[1] -1	0	0xfbe00000 - 0xfbffffff (0x200000) MX[B]
	[2] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[3] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[4] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[5] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[6] -1	0	0xda000000 - 0xdaffffff (0x1000000) MX[B](B)
	[7] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[9] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B](B)
	[10] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[13] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[14] -1	0	0x0000f000 - 0x0000f0ff (0x100) IX[B]
	[15] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[16] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[17] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
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
	[4] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B]
	[5] -1	0	0xfbe00000 - 0xfbffffff (0x200000) MX[B]
	[6] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[7] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[8] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[9] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[10] -1	0	0xda000000 - 0xdaffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[12] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[13] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[19] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f0ff (0x100) IX[B]
	[21] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[22] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[23] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
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
(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(EE) No drivers available.

Fatal server error:
no screens found

```

But if i do sudo modprobe ndivia i dont get any errors... and sudo dmesg shows:

```
[ 1703.986068] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-8762  Mon May 15 13:58:14 PDT 2006

```

So... i dont know what's the problem.
Thanks

---

### Post by vibhu on 2006-07-09
Did you try this for Nvidia :
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

Worked for me. Similar system configuration. 


However your config says :
> 
AMD Athlon 64 3000+ Core Venice
Abit KN8-Ultra
2x512 DDR400 Dual Channel (Geil kit)
MSI NX6600GT-TD128
SB X-FI XM

ASUS A4K Laptop
AMD Athlon 64 mobile 3200+
2*256 DDR 400
Mobo ASUS Nforce3-150
**Ati Radeon Mobility 9700**

Should you not be installing the ATI drivers ?
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28ATI.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28ATI.29)

---

### Post by songochain on 2006-07-09
My laptop has a ati card but my pc has a geforce 6600GT from MSI.
Thanks!

---

### Post by Teroedni on 2006-07-09
Open terminal

and write
```
sudo gedit /etc/modules
```

a text file comes up
it contains module it loads at startup
add nvidia there , save it and restart the computer.


If that dosent solve it i recomend you to ask in this thread
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

