---
title: "Video on Cube with Apple Studio Display (LCD) 17&quot;"
date: 2006-06-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jason C. on 2006-06-04
Hello all,

I posted this on another forum, but I think I was in the wrong place.  Here are the details.  Hello all,

I have been using Hoary on my Powerbook at work and was excited to install Linux on my mac at home. Unfortunately I am having problems getting the X windows server up and running. My hardware is a G4 Cube with a Rage ATI 128 Pro card and a Apple Studio Display 17" (LCD) connected throught the Apple Display Connector. After installing Breezy, X tries to start but fails on the error "Cannot read V_BIOS." After some searching on the web I found that many people have solved this problem by using the Option "FBDev" in the x config file. Sadly, this option causes framebuffering errors and the X server tells me "Screens found, but none have a usable configuration" (I can post the entire X log file if it is necessary). After Googling these errors I find that the solution to this is to turn FBDev off. So I am at a catch 22 . Any help with this problem is greatly appreciated. I was very excited to start using Linux and now my experiment is failing.

---

### Post by Jason C. on 2006-06-04
Okay, to provide additional info here is my Xorg.0.log file when using fbdev.  Note I do have a /dev/fb0, but /dev/fb[1-9] are not present.

Any help is very much appreciated.


X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010180225 [email]root@adare.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.12 ppc [ELF] 
Current Operating System: Linux wartyback 2.6.12-9-powerpc #1 Mon Oct 10 15:26:45 BST 2005 ppc
Build Date: 10 October 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-powerpc (buildd@adare) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 15:26:45 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jun  4 12:57:32 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Apple Studio"
(**) |   |-->Device "ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(II) Open APM successful
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
(II) PCI: 00:0b:0: chip 106b,0020 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:10:0: chip 1002,5046 card 0000,0000 rev 00 class 03,00,00 hdr 00
(II) PCI: 10:0b:0: chip 106b,001f card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 10:17:0: chip 106b,0022 card 0000,0000 rev 03 class ff,00,00 hdr 00
(II) PCI: 10:18:0: chip 106b,0019 card 0000,0000 rev 00 class 0c,03,10 hdr 00
(II) PCI: 10:19:0: chip 106b,0019 card 0000,0000 rev 00 class 0c,03,10 hdr 00
(II) PCI: 10:1a:0: chip 104c,8020 card 0000,0000 rev 00 class 0c,00,10 hdr 00
(II) PCI: 20:0b:0: chip 106b,001e card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 20:0f:0: chip 106b,0021 card 0000,0000 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:11:0), (0,0,32), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x00ffffff (0x1000000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 16: bridge is at (16:11:0), (16,16,32), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 16 I/O range:
	[0] -1	0	0x00000000 - 0x00ffffff (0x1000000) IX[B]
(II) Bus 16 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 16 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 32: bridge is at (32:11:0), (32,32,32), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 32 I/O range:
	[0] -1	0	0x00000000 - 0x00ffffff (0x1000000) IX[B]
(II) Bus 32 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 32 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(0:16:0) ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS rev 0, Mem @ 0x94000000/26, 0x90000000/14, I/O @ 0x0400/8, BIOS @ 0x90020000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x00ffffff (0x1000000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x00000000 - 0x00000000 (0x1) MX[B]
	[2] -1	0	0x00ffffff - 0x00ffffff (0x1) IX[B]
	[3] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[1] -1	0	0x80084000 - 0x80087fff (0x4000) MX[B]
	[2] -1	0	0x80080000 - 0x800807ff (0x800) MX[B]
	[3] -1	0	0x80081000 - 0x80081fff (0x1000) MX[B]
	[4] -1	0	0x80082000 - 0x80082fff (0x1000) MX[B]
	[5] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B]
	[6] -1	0	0x90020000 - 0x9003ffff (0x20000) MX[B](B)
	[7] -1	0	0x90000000 - 0x90003fff (0x4000) MX[B](B)
	[8] -1	0	0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
	[9] -1	0	0x00000400 - 0x000004ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[1] -1	0	0x80084000 - 0x80087fff (0x4000) MX[B]
	[2] -1	0	0x80080000 - 0x800807ff (0x800) MX[B]
	[3] -1	0	0x80081000 - 0x80081fff (0x1000) MX[B]
	[4] -1	0	0x80082000 - 0x80082fff (0x1000) MX[B]
	[5] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B]
	[6] -1	0	0x90020000 - 0x9003ffff (0x20000) MX[B](B)
	[7] -1	0	0x90000000 - 0x90003fff (0x4000) MX[B](B)
	[8] -1	0	0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
	[9] -1	0	0x00000400 - 0x000004ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x00000000 - 0x00000000 (0x1) MX[B]
	[2] -1	0	0x00ffffff - 0x00ffffff (0x1) IX[B]
	[3] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x00000000 - 0x00000000 (0x1) MX[B]
	[2] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[3] -1	0	0x80084000 - 0x80087fff (0x4000) MX[B]
	[4] -1	0	0x80080000 - 0x800807ff (0x800) MX[B]
	[5] -1	0	0x80081000 - 0x80081fff (0x1000) MX[B]
	[6] -1	0	0x80082000 - 0x80082fff (0x1000) MX[B]
	[7] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B]
	[8] -1	0	0x90020000 - 0x9003ffff (0x20000) MX[B](B)
	[9] -1	0	0x90000000 - 0x90003fff (0x4000) MX[B](B)
	[10] -1	0	0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
	[11] -1	0	0x00ffffff - 0x00ffffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[13] -1	0	0x00000400 - 0x000004ff (0x100) IX[B](B)
(WW) Ignoring request to load module GLcore
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
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
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
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
(II) LoadModule: "ati"
(II) Loading /usr/X11R6/lib/modules/drivers/ati_drv.o
(II) Module ati: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 6.5.6
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) ATI: ATI driver (version 6.5.6) for chipset: ati
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
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
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9200PRO 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9700 NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI RADEON 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireGL D1100 (RV370) 5B65 (PCIE),
	ATI Radeon Mobility M300 (M22) 5460 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI FireGL V5000,
	ATI MOBILITY FireGL V5000, ATI MOBILITY FireGL V5000,
	ATI MOBILITY RADEON X700, ATI MOBILITY RADEON X700,
	ATI RADEON X700 PRO, ATI RADEON X700 XT, ATI RADEON X700,
	ATI RADEON X700 SE, ATI RADEON X700 SE,
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI RADEON X800 SE,
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V7200 (R423) UQ (PCIE), ATI FireGL V5100 (R423) UR (PCIE),
	ATI FireGL V7100 (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100,
	ATI MOBILITY FireGL V5100, ATI MOBILITY RADEON X800,
	ATI MOBILITY RADEON X800 XT, ATI RADEON X800, ATI RADEON X800 XL,
	ATI RADEON R430 SE, ATI RADEON R430 XTP, ATI RADEON R480 4P,
	ATI RADEON R480 GL 16P, ATI RADEON R480 SE, ATI RADEON X850 PRO,
	ATI RADEON X850 XT, ATI RADEON X850 XT Platinum Edition,
	ATI RADEON X850 PRO, ATI RADEON X850 SE, ATI RADEON X850 XT,
	ATI RADEON X850 XT Platinum Edition
(II) Primary Device is: PCI 00:10:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)".
(--) Chipset ATI Rage 128 Pro GL PF (AGP) found
(II) Loading sub module "r128"
(II) LoadModule: "r128"
(II) Loading /usr/X11R6/lib/modules/drivers/r128_drv.o
(II) Module r128: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 4.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x00000000 - 0x00000000 (0x1) MX[B]
	[2] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[3] -1	0	0x80084000 - 0x80087fff (0x4000) MX[B]
	[4] -1	0	0x80080000 - 0x800807ff (0x800) MX[B]
	[5] -1	0	0x80081000 - 0x80081fff (0x1000) MX[B]
	[6] -1	0	0x80082000 - 0x80082fff (0x1000) MX[B]
	[7] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B]
	[8] -1	0	0x90020000 - 0x9003ffff (0x20000) MX[B](B)
	[9] -1	0	0x90000000 - 0x90003fff (0x4000) MX[B](B)
	[10] -1	0	0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
	[11] -1	0	0x00ffffff - 0x00ffffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[13] -1	0	0x00000400 - 0x000004ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x00000000 - 0x00000000 (0x1) MX[B]
	[2] -1	0	0xf5200000 - 0xf53fffff (0x200000) MX[B]
	[3] -1	0	0x80084000 - 0x80087fff (0x4000) MX[B]
	[4] -1	0	0x80080000 - 0x800807ff (0x800) MX[B]
	[5] -1	0	0x80081000 - 0x80081fff (0x1000) MX[B]
	[6] -1	0	0x80082000 - 0x80082fff (0x1000) MX[B]
	[7] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B]
	[8] -1	0	0x90020000 - 0x9003ffff (0x20000) MX[B](B)
	[9] -1	0	0x90000000 - 0x90003fff (0x4000) MX[B](B)
	[10] -1	0	0x94000000 - 0x97ffffff (0x4000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x00ffffff - 0x00ffffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[16] -1	0	0x00000400 - 0x000004ff (0x100) IX[B](B)
	[17] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[18] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) R128(0): PCI bus 0 card 16 func 0
(**) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(**) R128(0): Option "UseFBDev" "true"
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(**) R128(0): Using framebuffer device
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/X11R6/lib/modules/linux/libfbdevhw.a
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.0.2
	ABI class: X.Org Video Driver, version 0.7
(WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory
(EE) Unable to find a valid framebuffer device
(EE) R128(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
	(you may have to look at the server log to see warnings)
(II) UnloadModule: "ati"
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/X11R6/lib/modules/linux/libfbdevhw.a
(II) UnloadModule: "vgahw"
(II) Unloading /usr/X11R6/lib/modules/libvgahw.a
(II) UnloadModule: "r128"
(II) Unloading /usr/X11R6/lib/modules/drivers/r128_drv.o
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.X.Org](http://wiki.X.Org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

---

### Post by Jason C. on 2006-06-05
I've solved it!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! (yes, I am happy)

As it turns out, when I was installing ubuntu I could not get an image on the screen, so I passed the "video=ofonly" argument to the installer.  Unbeknownst to me, the yaboot loader was passing on this argument to the kernel as well.  This occured to me today when I was surfing the web, trying to uderstand why I kept getting the framebuffering errors.  I then discovered that with framebuffering and the ATI RAGE 128 cards, you have to pass the following to the kernel to get it to work: "video=aty128fb".  So, this evening I went into the yaboot.conf and indeed the video=ofonly argument was being passed to the bootloader.  Changed it to video=aty128fb, ran ybin -v and here I am posting from Firefox within Ubuntu.

Kick but.

Jason

---

