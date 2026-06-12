---
title: "Problems installing any Ubuntu"
date: 2009-03-15
forum: x86 64-bit Users
---

### Post by Jphenow on 2009-03-15
Ok, I've been using Ubuntu for about 2 years now, I wanted to try Kubuntu, cause it's been awhile. After Trying to install it the X won't start, even from the Live cd to get the install going. Here is a list of the Installs I've tried so far

Kubuntu 64Bit 8.04
Ubuntu x86 8.10
Kubuntu 64Bit 8.10
Ubuntu 64Bit 8.10
Kubuntu 64Bit 9.04 Alpha6 (Was crossing fingers that they fixed my bug)

On a few occasions after much editing of files and some steps I couldn't even rethink I've had an install. and after installing the Nvidia drivers I can get an X going, but at 640x480 on a 19" widescreen...sweet huh? Well after the last attempt (Jaunty alpha 6) I jumped through a few flaming hoops to remote scp myself the xorg log, I haven't been able to get much help from the community yet so maybe this log file will help something.

> 
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux ubuntu 2.6.28-9-generic #29-Ubuntu SMP Sun Mar 8 02:02:39 UTC 2009 x86_64
Build Date: 07 March 2009  02:19:24AM
xorg-server 2:1.6.0-0ubuntu1 (buildd@crested.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: [    0.001565] (--) probed, [    0.001591] (**) from config file, [    0.001613] (==) default setting,
	[    0.001634] (++) from command line, [    0.001655] (!!) notice, [    0.001675] (II) informational,
	[    0.001696] (WW) warning, [    0.001716] (EE) error, [    0.001736] (NI) not implemented, [    0.001756] (??) unknown.
[    0.001909] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Mar 15 18:31:16 2009
[    0.002043] (==) Using config file: "/etc/X11/xorg.conf"
[    0.002252] (==) No Layout section.  Using the first Screen section.
[    0.002277] (**) |-->Screen "Default Screen" (0)
[    0.002296] (**) |   |-->Monitor "Configured Monitor"
[    0.002783] (**) |   |-->Device "Configured Video Device"
[    0.002826] (==) Automatically adding devices
[    0.002844] (==) Automatically enabling devices
[    0.002972] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
[    0.003269] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    0.003284] (==) ModulePath set to "/usr/lib/xorg/modules"
[    0.003303] (II) Cannot locate a core pointer device.
[    0.003317] (II) Cannot locate a core keyboard device.
[    0.003330] (II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
[    0.003353] (II) Loader magic: 0xb40
[    0.003367] (II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
[    0.003420] (II) Loader running on linux
[    0.003440] (++) using VT number 7

[    0.089766] (--) PCI:*(0@2:0:0) nVidia Corporation GeForce 8500 GT rev 161, Mem @ 0xdf000000/16777216, 0xc0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
[    0.089993] (II) Open ACPI successful (/var/run/acpid.socket)
[    0.090038] (II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
[    0.091093] (II) LoadModule: "extmod"
[    0.092512] (II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
[    0.092930] (II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.092992] (II) Loading extension MIT-SCREEN-SAVER
[    0.093019] (II) Loading extension XFree86-VidModeExtension
[    0.093033] (II) Loading extension XFree86-DGA
[    0.093046] (II) Loading extension DPMS
[    0.093059] (II) Loading extension XVideo
[    0.093077] (II) Loading extension XVideo-MotionCompensation
[    0.093092] (II) Loading extension X-Resource
[    0.093107] (II) LoadModule: "dbe"
[    0.093898] (II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
[    0.094103] (II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.094164] (II) Loading extension DOUBLE-BUFFER
[    0.094179] (II) LoadModule: "glx"
[    0.095006] (II) Loading /usr/lib/xorg/modules/extensions//libglx.so
[    0.095398] (II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.095460] (==) AIGLX enabled
[    0.095484] (II) Loading extension GLX
[    0.095505] (II) LoadModule: "record"
[    0.096331] (II) Loading /usr/lib/xorg/modules/extensions//librecord.so
[    0.096538] (II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.096599] (II) Loading extension RECORD
[    0.096614] (II) LoadModule: "dri"
[    0.097402] (II) Loading /usr/lib/xorg/modules/extensions//libdri.so
[    0.097874] (II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.097935] (II) Loading extension XFree86-DRI
[    0.097955] (II) LoadModule: "dri2"
[    0.099586] (II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
[    0.099812] (II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.099864] (II) Loading extension DRI2
[    0.099882] (II) LoadModule: "vesa"
[    0.100538] (II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
[    0.100757] (II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
[    0.100838] (II) VESA: driver for VESA chipsets: vesa
[    0.102160] (II) Primary Device is: PCI 02@00:00:0
[    0.102253] (II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
[    0.144950] (II) Loading sub module "vbe"
[    0.144973] (II) LoadModule: "vbe"
[    0.145206] (II) Loading /usr/lib/xorg/modules//libvbe.so
[    0.145449] (II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
[    0.145516] (II) Loading sub module "int10"
[    0.145531] (II) LoadModule: "int10"
[    0.145706] (II) Loading /usr/lib/xorg/modules//libint10.so
[    0.145998] (II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
[    0.146070] (II) VESA(0): initializing int10
[    0.153290] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    0.359126] (II) VESA(0): VESA BIOS detected
[    0.359187] (II) VESA(0): VESA VBE Version 3.0
[    0.359203] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    0.359241] (II) VESA(0): VESA VBE OEM: NVIDIA
[    0.359256] (II) VESA(0): VESA VBE OEM Software Rev: 96.134
[    0.359271] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    0.359285] (II) VESA(0): VESA VBE OEM Product: G86 Board - p402h00 
[    0.359299] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    0.805125] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    0.805173] (==) VESA(0): Depth 24, [    0.805190] (--) framebuffer bpp 32
[    0.805210] (==) VESA(0): RGB weight 888
[    0.805229] (==) VESA(0): Default visual is TrueColor
[    0.805248] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    0.805305] (II) Loading sub module "ddc"
[    0.805321] (II) LoadModule: "ddc"
[    0.805361] (II) Module "ddc" already built-in
[    0.883352] (II) VESA(0): VESA VBE DDC supported
[    0.883373] (II) VESA(0): VESA VBE DDC Level none
[    0.883389] (II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
[    1.237370] (II) VESA(0): VESA VBE DDC read failed
[    1.237382] (II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 101 (640x480)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 102 (800x600)
	ModeAttributes: 0x33f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 100
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 103 (800x600)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 104 (1024x768)
	ModeAttributes: 0x33f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 128
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 105 (1024x768)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 10e (320x200)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 10f (320x200)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 111 (640x480)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 112 (640x480)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 114 (800x600)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 115 (800x600)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 117 (1024x768)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 118 (1024x768)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 130 (320x200)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 62
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 62
	LinNumberOfImagePages: 62
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 131 (320x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 132 (320x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 133 (320x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 134 (320x240)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 135 (320x240)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 19
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 19
	LinNumberOfImagePages: 19
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 136 (320x240)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 13d (640x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 13e (640x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 160 (1280x800)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 161 (1280x800)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 162 (768x480)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008ab8
	BytesPerScanline: 768
	XResolution: 768
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 8
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xdd000000
	LinBytesPerScanLine: 768
	BnkNumberOfImagePages: 8
	LinNumberOfImagePages: 8
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000

[    1.334798] (II) VESA(0): Total Memory: 224 64KB banks (14336kB)
[    1.334829] (II) VESA(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
[    1.334843] (II) VESA(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
[    1.334855] (WW) VESA(0): Unable to estimate virtual size
[    1.334876] (II) VESA(0): Not using built-in mode "1280x800" (no mode of this name)
[    1.334885] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    1.334893] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    1.334901] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    1.334913] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[    1.334924] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[    1.334933] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    1.334941] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    1.334949] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    1.334957] (II) VESA(0): Configured Monitor: Using hsync range of 31.50-37.90 kHz
[    1.334965] (II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-70.00 Hz
[    1.334974] (WW) VESA(0): Unable to estimate virtual size
[    1.335021] (II) VESA(0): Not using built-in mode "1280x800" (hsync out of range)
[    1.335048] (II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
[    1.335090] (II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
[    1.335116] (II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
[    1.335145] (II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
[    1.335172] (II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[    1.335184] (--) VESA(0): Virtual size is 800x600 (pitch 800)
[    1.335191] (**) VESA(0): *Built-in mode "800x600"
[    1.335198] (**) VESA(0): *Built-in mode "640x480"
[    1.335207] (==) VESA(0): DPI set to (96, 96)
[    1.335233] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
[    1.336311] (II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
[    1.337388] (**) VESA(0): Using "Shadow Framebuffer"
[    1.337395] (II) Loading sub module "shadow"
[    1.337402] (II) LoadModule: "shadow"
[    1.337503] (II) Loading /usr/lib/xorg/modules//libshadow.so
[    1.337636] (II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
[    1.337659] (II) Loading sub module "fb"
[    1.337665] (II) LoadModule: "fb"
[    1.337731] (II) Loading /usr/lib/xorg/modules//libfb.so
[    1.337857] (II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
[    1.337953] (==) Depth 24 pixmap format is 32 bpp
[    1.337961] (II) do I need RAC?  No, I don't.
[    1.337971] (II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
[    1.338389] (II) Loading sub module "int10"
[    1.338395] (II) LoadModule: "int10"
[    1.338464] (II) Reloading /usr/lib/xorg/modules//libint10.so
[    1.338476] (II) VESA(0): initializing int10
[    1.342737] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    1.456948] (II) VESA(0): VESA BIOS detected
[    1.456960] (II) VESA(0): VESA VBE Version 3.0
[    1.456967] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    1.456973] (II) VESA(0): VESA VBE OEM: NVIDIA
[    1.456980] (II) VESA(0): VESA VBE OEM Software Rev: 96.134
[    1.456992] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    1.456999] (II) VESA(0): VESA VBE OEM Product: G86 Board - p402h00 
[    1.457005] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    1.457334] (II) VESA(0): virtual address = 0x7f95b5228000,
	physical address = 0xdd000000, size = 14680064
[    1.735914] (==) VESA(0): Default visual is TrueColor
[    1.736028] (==) VESA(0): Backing store disabled
[    1.736163] (II) VESA(0): DPMS enabled
[    1.736186] (==) RandR enabled
[    1.751678] (II) Initializing built-in extension Generic Event Extension
[    1.751687] (II) Initializing built-in extension SHAPE
[    1.751693] (II) Initializing built-in extension MIT-SHM
[    1.751699] (II) Initializing built-in extension XInputExtension
[    1.751706] (II) Initializing built-in extension XTEST
[    1.751712] (II) Initializing built-in extension BIG-REQUESTS
[    1.751718] (II) Initializing built-in extension SYNC
[    1.751724] (II) Initializing built-in extension XKEYBOARD
[    1.751730] (II) Initializing built-in extension XC-MISC
[    1.751736] (II) Initializing built-in extension SECURITY
[    1.751742] (II) Initializing built-in extension XINERAMA
[    1.751748] (II) Initializing built-in extension XFIXES
[    1.751755] (II) Initializing built-in extension RENDER
[    1.751761] (II) Initializing built-in extension RANDR
[    1.751767] (II) Initializing built-in extension COMPOSITE
[    1.751773] (II) Initializing built-in extension DAMAGE
[    1.758698] (II) AIGLX: Screen 0 is not DRI2 capable
[    1.758720] (II) AIGLX: Screen 0 is not DRI capable
[    1.765865] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    1.765878] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    1.839849] (II) config/hal: Adding input device Logitech USB Receiver
[    1.839884] (II) LoadModule: "evdev"
[    1.840053] (II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
[    1.840209] (II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
[    1.840266] (**) Logitech USB Receiver: always reports core events
[    1.840276] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[    1.854246] (II) Logitech USB Receiver: Found 9 mouse buttons
[    1.854254] (II) Logitech USB Receiver: Found x and y relative axes
[    1.854260] (II) Logitech USB Receiver: Found keys
[    1.854266] (II) Logitech USB Receiver: Configuring as mouse
[    1.854272] (II) Logitech USB Receiver: Configuring as keyboard
[    1.854289] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    1.854296] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    1.854316] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    1.854333] (**) Option "xkb_rules" "evdev"
[    1.854345] (**) Logitech USB Receiver: xkb_rules: "evdev"
[    1.854352] (**) Option "xkb_model" "pc105"
[    1.854364] (**) Logitech USB Receiver: xkb_model: "pc105"
[    1.854370] (**) Option "xkb_layout" "us"
[    1.854382] (**) Logitech USB Receiver: xkb_layout: "us"
[    1.900436] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    1.900457] (**) Logitech USB Receiver: (accel) filter chain progression: 2.00
[    1.900470] (**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
[    1.900484] (**) Logitech USB Receiver: (accel) set acceleration profile 0
[    1.902472] (II) config/hal: Adding input device Macintosh mouse button emulation
[    1.902524] (**) Macintosh mouse button emulation: always reports core events
[    1.902533] (**) Macintosh mouse button emulation: Device: "/dev/input/event2"
[    1.914253] (II) Macintosh mouse button emulation: Found 3 mouse buttons
[    1.914261] (II) Macintosh mouse button emulation: Found x and y relative axes
[    1.914268] (II) Macintosh mouse button emulation: Configuring as mouse
[    1.914280] (**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
[    1.914294] (**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    1.914316] (II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
[    1.914338] (**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
[    1.914345] (**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
[    1.914357] (**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
[    1.914368] (**) Macintosh mouse button emulation: (accel) set acceleration profile 0
[    1.915914] (II) config/hal: Adding input device Logitech USB Receiver
[    1.915944] (**) Logitech USB Receiver: always reports core events
[    1.915952] (**) Logitech USB Receiver: Device: "/dev/input/event4"
[    1.926235] (II) Logitech USB Receiver: Found keys
[    1.926243] (II) Logitech USB Receiver: Configuring as keyboard
[    1.926254] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    1.926270] (**) Option "xkb_rules" "evdev"
[    1.926282] (**) Logitech USB Receiver: xkb_rules: "evdev"
[    1.926289] (**) Option "xkb_model" "pc105"
[    1.926301] (**) Logitech USB Receiver: xkb_model: "pc105"
[    1.926307] (**) Option "xkb_layout" "us"
[    1.926319] (**) Logitech USB Receiver: xkb_layout: "us"
[    1.973309] (II) config/hal: Adding input device Logitech USB-PS/2 Optical Mouse
[    1.973354] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[    1.973363] (**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event3"
[    1.986266] (II) Logitech USB-PS/2 Optical Mouse: Found 8 mouse buttons
[    1.986274] (II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[    1.986280] (II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[    1.986292] (**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[    1.986299] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    1.986314] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[    1.986338] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[    1.986345] (**) Logitech USB-PS/2 Optical Mouse: (accel) filter chain progression: 2.00
[    1.986358] (**) Logitech USB-PS/2 Optical Mouse: (accel) filter stage 0: 20.00 ms
[    1.986370] (**) Logitech USB-PS/2 Optical Mouse: (accel) set acceleration profile 0
[   84.927294] (II) Logitech USB Receiver: Close
[   84.927410] (II) UnloadModule: "evdev"
[   84.955325] (II) Macintosh mouse button emulation: Close
[   84.955386] (II) UnloadModule: "evdev"
[   84.975314] (II) Logitech USB Receiver: Close
[   84.975415] (II) UnloadModule: "evdev"
[   85.011313] (II) Logitech USB-PS/2 Optical Mouse: Close
[   85.011376] (II) UnloadModule: "evdev"
[   85.565609] (II) Open ACPI successful (/var/run/acpid.socket)
[   85.565641] (II) APM registered successfully
[   85.565659] (II) Loading sub module "int10"
[   85.565666] (II) LoadModule: "int10"
[   85.565915] (II) Reloading /usr/lib/xorg/modules//libint10.so
[   85.565945] (II) VESA(0): initializing int10
[   85.570179] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[   85.684355] (II) VESA(0): VESA BIOS detected
[   85.684366] (II) VESA(0): VESA VBE Version 3.0
[   85.684372] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[   85.684379] (II) VESA(0): VESA VBE OEM: NVIDIA
[   85.684385] (II) VESA(0): VESA VBE OEM Software Rev: 96.134
[   85.684392] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[   85.684399] (II) VESA(0): VESA VBE OEM Product: G86 Board - p402h00 
[   85.684405] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[   85.684737] (II) VESA(0): virtual address = 0x7f95b5228000,
	physical address = 0xdd000000, size = 14680064
[   85.947823] (==) VESA(0): Default visual is TrueColor
[   85.947968] (II) VESA(0): DPMS enabled
[   85.947981] (==) RandR enabled
[   85.954552] (II) AIGLX: Screen 0 is not DRI2 capable
[   85.954566] (II) AIGLX: Screen 0 is not DRI capable
[   85.961652] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[   85.961663] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   85.978717] (EE) XKB: No components provided for device Virtual core keyboard
[   85.978764] (WW) Couldn't load XKB keymap, falling back to pre-XKB keymap
[config/dbus] couldn't register object path
[   85.987623] (II) config/hal: Adding input device Logitech USB Receiver
[   85.987662] (**) Logitech USB Receiver: always reports core events
[   85.987671] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[   85.999241] (II) Logitech USB Receiver: Found 9 mouse buttons
[   85.999250] (II) Logitech USB Receiver: Found x and y relative axes
[   85.999257] (II) Logitech USB Receiver: Found keys
[   85.999263] (II) Logitech USB Receiver: Configuring as mouse
[   85.999269] (II) Logitech USB Receiver: Configuring as keyboard
[   85.999282] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[   85.999289] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   85.999316] (**) Option "xkb_rules" "evdev"
[   85.999331] (**) Logitech USB Receiver: xkb_rules: "evdev"
[   85.999338] (**) Option "xkb_model" "pc105"
[   85.999350] (**) Logitech USB Receiver: xkb_model: "pc105"
[   85.999357] (**) Option "xkb_layout" "us"
[   85.999369] (**) Logitech USB Receiver: xkb_layout: "us"
[   86.047029] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[   86.047051] (**) Logitech USB Receiver: (accel) filter chain progression: 2.00
[   86.047065] (**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
[   86.047078] (**) Logitech USB Receiver: (accel) set acceleration profile 0
[   86.048960] (II) config/hal: Adding input device Macintosh mouse button emulation
[   86.049106] (**) Macintosh mouse button emulation: always reports core events
[   86.049115] (**) Macintosh mouse button emulation: Device: "/dev/input/event2"
[   86.059253] (II) Macintosh mouse button emulation: Found 3 mouse buttons
[   86.059262] (II) Macintosh mouse button emulation: Found x and y relative axes
[   86.059269] (II) Macintosh mouse button emulation: Configuring as mouse
[   86.059282] (**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
[   86.059290] (**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   86.059326] (**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
[   86.059334] (**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
[   86.059345] (**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
[   86.059357] (**) Macintosh mouse button emulation: (accel) set acceleration profile 0
[   86.060958] (II) config/hal: Adding input device Logitech USB Receiver
[   86.060985] (**) Logitech USB Receiver: always reports core events
[   86.060993] (**) Logitech USB Receiver: Device: "/dev/input/event4"
[   86.071247] (II) Logitech USB Receiver: Found keys
[   86.071255] (II) Logitech USB Receiver: Configuring as keyboard
[   86.071278] (**) Option "xkb_rules" "evdev"
[   86.071292] (**) Logitech USB Receiver: xkb_rules: "evdev"
[   86.071298] (**) Option "xkb_model" "pc105"
[   86.071310] (**) Logitech USB Receiver: xkb_model: "pc105"
[   86.071317] (**) Option "xkb_layout" "us"
[   86.071329] (**) Logitech USB Receiver: xkb_layout: "us"
[   86.120336] (II) config/hal: Adding input device Logitech USB-PS/2 Optical Mouse
[   86.120386] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[   86.120396] (**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event3"
[   86.131266] (II) Logitech USB-PS/2 Optical Mouse: Found 8 mouse buttons
[   86.131275] (II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[   86.131281] (II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[   86.131294] (**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[   86.131301] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   86.131341] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[   86.131350] (**) Logitech USB-PS/2 Optical Mouse: (accel) filter chain progression: 2.00
[   86.131362] (**) Logitech USB-PS/2 Optical Mouse: (accel) filter stage 0: 20.00 ms
[   86.131374] (**) Logitech USB-PS/2 Optical Mouse: (accel) set acceleration profile 0
[  101.323356] (II) Logitech USB Receiver: Close
[  101.323457] (II) UnloadModule: "evdev"
[  101.355312] (II) Macintosh mouse button emulation: Close
[  101.355373] (II) UnloadModule: "evdev"
[  101.375307] (II) Logitech USB Receiver: Close
[  101.375399] (II) UnloadModule: "evdev"
[  101.403566] (II) Logitech USB-PS/2 Optical Mouse: Close
[  101.403627] (II) UnloadModule: "evdev"

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x26) [0x4f1916]
1: /usr/bin/X(xf86SigHandler+0x41) [0x485a91]
2: /lib/libc.so.6 [0x7f95b85bf040]
3: /usr/bin/X(DamageUnregister+0x33) [0x538d13]
4: /usr/lib/xorg/modules//libshadow.so(shadowRemove+0x3b) [0x7f95b624a37b]
5: /usr/lib/xorg/modules//libshadow.so [0x7f95b624a874]
6: /usr/bin/X [0x5068f9]
7: /usr/bin/X [0x536b53]
8: /usr/bin/X(main+0x44c) [0x433e6c]
9: /lib/libc.so.6(__libc_start_main+0xe6) [0x7f95b85aa5a6]
10: /usr/bin/X [0x433269]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log

Thanks in advance, I really need help guys, I need to get my Linux back up and running. Also I'll say that between this whole ordeal of switching I can't think of making any changes that would have created a problem out of thin air. Didn't move any hardware around or anything.

[EDIT]
Oh I should probably say that I picked up this log while trying to get into an X for the installation of Jaunty. Only mod I made on the CD was I added "Driver "vesa"" to the xorg.conf which got some things showing but not actual desktop. "nv" would not work and Idealy I'm sure I would want an actual Nvidia driver, but that has failed me so far, as I said earlier.

---

### Post by 3Miro on 2009-03-15
Kubuntu has stability issues right now. I am using it just because of the power that KDE 4.2 brings, other than that it is less stable than Gnome.

How did you try installing the thing, by upgrading Ubuntu or by making a clean set up. Does Ubuntu Live CD start up fine? You mentioned that you have been using Ubuntu up until now, did you have any trouble installing that one?

---

### Post by Jphenow on 2009-03-15
I don't recall this many issues in any original installs. No the Live CD for both ubuntu and kubuntu are having problems, I can get it to work if I change the primary video device to onboard in my BIOS. Only issue with that is that I will then not be able to use my DVI and I'd be using a VGA loaner. I felt like doing a clean install, because about every 2 major upgrades I think it's good practice to do a clean install.

My most recent tries included changing that BIOS feature to Onboard, getting it installed, updated and adding the driver for nvidia. then I restared and it didn't work! Then I even went back to try and change the Primary video device to PCI-Express. Still no go...this killing me. Everytime I try to actually use the Video card (outside of Windows XP) ubuntu/kubuntu flip out on me... No good

---

