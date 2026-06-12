---
title: "xorg.conf settings ineffective in Kubuntu 8.10? (2048x1536 CRT)"
date: 2009-03-21
forum: x86 64-bit Users
---

### Post by dh003i on 2009-03-21
I'm having problems getting my Sony GDM-F520 2048x1536 CRT to work properly under Kubuntu 8.10. I'm using the the head version (as of 3/16/2009) of the radeonhd drivers, and a Radeon HD4670 GPU. 

I believe I have my xorg.conf file setup right, so why isn't it working? I think it's because of all this new "easy to use" stuff ignoring my xorg.conf settings. Here is some relevant information:

I tried what you said, it still doesn't work. Now, I modified my xorg.conf file (there were a few errors detected in /var/log/Xorg.conf.0.log), and it will load KDE, but still at this awful low resolution (1152x864). 

It is like it is ignoring all of my settings for 2048x1536! I don't like xrandr. 

**/var/log/Xorg.conf.0.log**
```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux davidjheinrich 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 20 17:29:32 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Sony GDM-F520"
(**) |   |-->Device "ATI Radeon HD4670"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7b7320
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0@1:0:0) ATI Technologies Inc RV730XT [Radeon HD 4670] rev 0, Mem @ 0xd0000000/268435456, 0xfe8e0000/65536, I/O @ 0x0000b000/256, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
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
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "radeonhd"

(II) Loading /usr/lib/xorg/modules/drivers//radeonhd_drv.so
(II) Module radeonhd: vendor="AMD GPG"
	compiled for 1.5.2, module version = 1.2.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) RADEONHD: X driver for the following AMD GPG (ATI) graphics devices:
	RV505 : Radeon X1550, X1550 64bit.
	RV515 : Radeon X1300, X1550, X1600; FireGL V3300, V3350.
	RV516 : Radeon X1300, X1550, X1550 64-bit, X1600; FireMV 2250.
	R520  : Radeon X1800; FireGL V5300, V7200, V7300, V7350.
	RV530 : Radeon X1300 XT, X1600, X1600 Pro, X1650; FireGL V3400, V5200.
	RV535 : Radeon X1300, X1650.
	RV550 : Radeon X2300 HD.
	RV560 : Radeon X1650.
	RV570 : Radeon X1950, X1950 GT; FireGL V7400.
	R580  : Radeon X1900, X1950; AMD Stream Processor.
	R600  : Radeon HD 2900 GT/Pro/XT; FireGL V7600/V8600/V8650.
	RV610 : Radeon HD 2350, HD 2400 Pro/XT, HD 2400 Pro AGP; FireGL V4000.
	RV620 : Radeon HD 3450, HD 3470.
	RV630 : Radeon HD 2600 LE/Pro/XT, HD 2600 Pro/XT AGP; Gemini RV630;
		FireGL V3600/V5600.
	RV635 : Radeon HD 3650, HD 3670.
	RV670 : Radeon HD 3690, 3850, HD 3870, FireGL V7700, FireStream 9170.
	R680  : Radeon HD 3870 X2.
	M52   : Mobility Radeon X1300.
	M54   : Mobility Radeon X1400; M54-GL.
	M56   : Mobility Radeon X1600; Mobility FireGL V5200.
	M58   : Mobility Radeon X1800, X1800 XT; Mobility FireGL V7100, V7200.
	M62   : Mobility Radeon X1350.
	M64   : Mobility Radeon X1450, X2300.
	M66   : Mobility Radeon X1700, X1700 XT; FireGL V5250.
	M68   : Mobility Radeon X1900.
	M71   : Mobility Radeon HD 2300.
	M72   : Mobility Radeon HD 2400; Radeon E2400.
	M74   : Mobility Radeon HD 2400 XT.
	M76   : Mobility Radeon HD 2600;
		(Gemini ATI) Mobility Radeon HD 2600 XT.
	M82   : Mobility Radeon HD 3400.
	M86   : Mobility Radeon HD 3650, HD 3670, Mobility FireGL V5700.
	M88   : Mobility Radeon HD 3850, HD 3850 X2, HD 3870, HD3870 X2.
	RS600 : Radeon Xpress 1200, Xpress 1250.
	RS690 : Radeon X1200, X1250, X1270.
	RS740 : RS740, RS740M.
	RS780 : Radeon HD 3100/3200/3300 Series.
	RV770 : Radeon HD 4800 Series; Everest, K2, Denali ATI FirePro.
	R700  : Radeon R700.
	M98   : Radeon M98 Mobility.
	RV730 : Radeon HD4670, HD4650.
	M96   : Radeon M96 Mobility.
	RV710 : Radeon HD4570, HD4350.

(II) RADEONHD: version 1.2.4, built from git branch master, commit d9c8f9ce

(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) RADEONHD(0): Depth 24, (--) framebuffer bpp 32
(**) RADEONHD(0): Option "AccelMethod" "exa"
(**) RADEONHD(0): Option "DRI" "on"
(**) RADEONHD(0): Selected EXA 2D acceleration.
(II) RADEONHD(0): Unknown card detected: 0x9490:0x1462:0x1590.
	If - and only if - your card does not work or does not work optimally
	please contact radeonhd@opensuse.org to help rectify this.
	Use the subject: 0x9490:0x1462:0x1590: <name of board>
	and *please* describe the problems you are seeing
	in your message.
(--) RADEONHD(0): Detected an RV730 on an unidentified card
(II) RADEONHD(0): Mapped IO @ 0xfe8e0000 to 0x7f613b562000 (size 0x00010000)
(II) RADEONHD(0): PCIE Card Detected
(II) RADEONHD(0): Getting BIOS copy from legacy VBIOS location
(II) RADEONHD(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1462 SubsystemID: 0x1590
	IOBaseAddress: 0xb000
	Filename: Test.bin    
	BIOS Bootup Message: 
113-MSITV159MS.100-AB73100-100-MI RV730 GDDR3 128BIT 750E/1000M               
(II) RADEONHD(0): Analog TV Default Mode: 1
(II) RADEONHD(0): Found default TV Mode NTSC
(II) RADEONHD(0): The detected amount of videoram exceeds the PCI BAR aperture.
(II) RADEONHD(0): Using only 262144kB of the total 524288kB.
(--) RADEONHD(0): VideoRAM: 262144 kByte
(II) RADEONHD(0): Framebuffer space used by Firmware (kb): 20
(II) RADEONHD(0): Start of VRAM area used by Firmware: 0x7ffec
(II) RADEONHD(0): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEONHD(0): AtomBIOS VRAM scratch base: 0x7ffec
(WW) RADEONHD(0): rhdAtomAllocateFbScratch: FW FB scratch area not located at the end of VRAM. Scratch End: 0x84fec VRAM End: 0x10000000
(II) RADEONHD(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEONHD(0): Default Engine Clock: 750000
(II) RADEONHD(0): Default Memory Clock: 1000000
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Input: 16000
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Input: 6000
(II) RADEONHD(0): Maximum Pixel Clock: 400000
(II) RADEONHD(0): Reference Clock: 27000
(WW) RADEONHD(0): Direct rendering for R600 and up forced on - This is NOT officially supported yet and may cause instability or lockups
(II) RADEONHD(0): Found libdri 5.4.0.
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEONHD(0): Found libdrm 1.3.0.
(II) RADEONHD(0): Found radeon drm 1.29.0.
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEONHD(0): Reference Clock: 27000
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f90
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f90
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 0" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f94
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f94
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 1" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f98
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f98
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 2" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f88
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f88
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 3" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1fc4
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1fc4
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 4" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1fe8
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1fe8
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 5" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) RADEONHD(0): Detected VGA mode.
(**) RADEONHD(0): Using AtomBIOS for Crtcs
(**) RADEONHD(0): Using AtomBIOS for PLLs
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEONHD(0): Maximum Pixel Clock: 400000
(II) RADEONHD(0): Reference Clock: 27000
(II) RADEONHD(0): rhdAtomSetPixelClockVersion returned version 3 for index 0xc
(II) RADEONHD(0): rhdAtomSetPixelClockVersion returned version 3 for index 0xc
(II) RADEONHD(0): FB: Allocated Cursor Image at offset 0x00000000 (size = 0x00004000)
(II) RADEONHD(0): FB: Allocated Cursor Image at offset 0x00004000 (size = 0x00004000)
(II) RADEONHD(0): Connector[0] {RHD_CONNECTOR_DVI, "DUAL_LINK_DVI_I CRT2 DFP2", RHD_DDC_4, RHD_HPD_1, { RHD_OUTPUT_UNIPHYC, RHD_OUTPUT_DACB } }
(II) RADEONHD(0): Connector[1] {RHD_CONNECTOR_DVI, "DUAL_LINK_DVI_I CRT1 DFP1", RHD_DDC_3, RHD_HPD_0, { RHD_OUTPUT_UNIPHYA, RHD_OUTPUT_DACA } }
(**) RADEONHD(0): Using AtomBIOS for Outputs
(EE) RADEONHD(0): RHDHdmiInit: unknown HDMI output type
(II) RADEONHD(0): rhdAtomSelectCrtcSourceVersion returned version 2 for index 0x2a
(--) RADEONHD(0): Attaching Output AtomOutputUniphyC to Connector DVI-I 1
(**) RADEONHD(0): Using AtomBIOS for Outputs
(II) RADEONHD(0): rhdAtomSelectCrtcSourceVersion returned version 2 for index 0x2a
(--) RADEONHD(0): Attaching Output AtomOutputDACB to Connector DVI-I 1
(**) RADEONHD(0): Using AtomBIOS for Outputs
(II) RADEONHD(0): rhdAtomSelectCrtcSourceVersion returned version 2 for index 0x2a
(--) RADEONHD(0): Attaching Output AtomOutputUniphyA to Connector DVI-I 2
(**) RADEONHD(0): Using AtomBIOS for Outputs
(II) RADEONHD(0): rhdAtomSelectCrtcSourceVersion returned version 2 for index 0x2a
(--) RADEONHD(0): Attaching Output AtomOutputDACA to Connector DVI-I 2
(II) RADEONHD(0): RandR: Adding RRoutput DVI-I_1/digital for Output AtomOutputUniphyC
(II) RADEONHD(0): RandR: Adding RRoutput DVI-I_1/analog for Output AtomOutputDACB
(II) RADEONHD(0): RandR: Adding RRoutput DVI-I_2/digital for Output AtomOutputUniphyA
(II) RADEONHD(0): RandR: Adding RRoutput DVI-I_2/analog for Output AtomOutputDACA
(II) RADEONHD(0): Output DVI-I_1/digital using monitor section Sony GDM-F520
(II) RADEONHD(0): Output DVI-I_1/digital has no monitor section
(II) RADEONHD(0): Output DVI-I_1/analog has no monitor section
(II) RADEONHD(0): Output DVI-I_2/digital has no monitor section
(II) RADEONHD(0): Output DVI-I_2/analog has no monitor section
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: none
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Setting AtomOutputDACA to incoherent
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): Output DVI-I_1/digital disconnected
(II) RADEONHD(0): Output DVI-I_1/analog disconnected
(II) RADEONHD(0): Output DVI-I_2/digital disconnected
(II) RADEONHD(0): Output DVI-I_2/analog connected
(II) RADEONHD(0): Using fuzzy aspect match for initial modes
(II) RADEONHD(0): Output DVI-I_2/analog using initial mode 1152x864
(II) RADEONHD(0): RandR 1.2 support enabled
(==) RADEONHD(0): RGB weight 888
(==) RADEONHD(0): Default visual is TrueColor
(==) RADEONHD(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEONHD(0): Using 2048x1536 Framebuffer with 2048 pitch
(II) RADEONHD(0): FB: Allocated ScanoutBuffer at offset 0x00008000 (size = 0x00C00000)
(**) RADEONHD(0): Display dimensions: (406, 303) mm
(**) RADEONHD(0): DPI set to (128, 128)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "exa"
(II) LoadModule: "exa"

(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEONHD(0): FB: Allocated Offscreen Buffer at offset 0x00C08000 (size = 0x01998000)
(II) RADEONHD(0): FB: Allocated DRI Back Buffer at offset 0x025A0000 (size = 0x00C00000)
(II) RADEONHD(0): FB: Allocated DRI Depth Buffer at offset 0x031A0000 (size = 0x00C00000)
(II) RADEONHD(0): FB: Allocated GART table at offset 0x0FFF0000 (size = 0x00010000, end of FB)
(II) RADEONHD(0): FB: Allocated DRI Textures at offset 0x03DA0000 (size = 0x0C000000)
(II) RADEONHD(0): Using 16 MB GART aperture
(II) RADEONHD(0): Using 2 MB for the ring buffer
(II) RADEONHD(0): Using 2 MB for vertex/indirect buffers
(II) RADEONHD(0): Using 12 MB for GART textures
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) RADEONHD(0): Mapped IO @ 0xfe8e0000 to 0x7f613b562000 (size 0x00010000)
(II) RADEONHD(0): Mapped FB @ 0xd0000000 to 0x7f61278c3000 (size 0x10000000)
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEONHD(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEONHD(0): [drm] framebuffer handle = 0xd0000000
(II) RADEONHD(0): [drm] added 1 reserved context for kernel
(II) RADEONHD(0): X context handle = 0x1
(II) RADEONHD(0): [drm] installed DRM signal handler
(II) RADEONHD(0): [pci] 16384 kB allocated with handle 0x1256d200
(II) RADEONHD(0): [pci] ring handle = 0x1effe000
(II) RADEONHD(0): [pci] Ring mapped at 0x7f61276c2000
(II) RADEONHD(0): [pci] Ring contents 0x00000000
(II) RADEONHD(0): [pci] ring read ptr handle = 0x2efff000
(II) RADEONHD(0): [pci] Ring read ptr mapped at 0x7f613b517000
(II) RADEONHD(0): [pci] Ring read ptr contents 0x00000000
(II) RADEONHD(0): [pci] vertex/indirect buffers handle = 0x1efff000
(II) RADEONHD(0): [pci] Vertex/indirect buffers mapped at 0x7f61274c2000
(II) RADEONHD(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEONHD(0): [pci] GART texture map handle = 0x1f000000
(II) RADEONHD(0): [pci] GART Texture map mapped at 0x7f6126902000
(II) RADEONHD(0): [drm] register handle = 0xfe8e0000
(II) RADEONHD(0): [dri] Visual configs initialized
(II) RADEONHD(0): [DRI] installation complete
(II) RADEONHD(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEONHD(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEONHD(0): [drm] dma control initialized, using IRQ 16
(II) RADEONHD(0): [drm] Initialized kernel GART heap manager, 12320768
(II) RADEONHD(0): Direct rendering enabled
(II) RADEONHD(0): Using DRM Command Processor (indirect) for acceleration.
(II) EXA(0): Offscreen pixmap area of 26836992 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II)         DownloadFromScreen
(==) RADEONHD(0): Backing store disabled
(==) RADEONHD(0): Silken mouse enabled
(II) RADEONHD(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling DAC2OutputControl
(II) RADEONHD(0): DAC2OutputControl Successful
(II) RADEONHD(0): Calling DACBEncoderControl
(II) RADEONHD(0): DACBEncoderControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling DACAEncoderControl
(II) RADEONHD(0): DACAEncoderControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): On Crtc 0 Setting 60.0 Hz Mode: Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync
(II) RADEONHD(0): Calling SetCRTC_Timing
(II) RADEONHD(0): SetCRTC_Timing Successful
(II) RADEONHD(0): CallingSetCRTC_OverScan
(II) RADEONHD(0): Set CRTC_OverScan Successful
(II) RADEONHD(0): Calling EnableScaler
(II) RADEONHD(0): EnableScaler Successful
(II) RADEONHD(0): Calling SetPixelClock
(II) RADEONHD(0): SetPixelClock Successful
(II) RADEONHD(0): Calling SelectCRTCSource
(II) RADEONHD(0): SelectCRTCSource Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling DACAEncoderControl
(II) RADEONHD(0): DACAEncoderControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling DAC2OutputControl
(II) RADEONHD(0): DAC2OutputControl Successful
(II) RADEONHD(0): Calling DACBEncoderControl
(II) RADEONHD(0): DACBEncoderControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): RHDAudioSetSupported: config 0x60040 codec 0x1
(II) RADEONHD(0): DPMS enabled
(II) RADEONHD(0): Xv: Textured Video initialised.
(--) RandR disabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(EE) AIGLX error: dlopen of /usr/lib/dri/r600_dri.so failed (/usr/lib/dri/r600_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) RADEONHD(0): Setting screen physical size to 304 x 228
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found 1 mouse buttons
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found 16 mouse buttons
(II) Logitech USB Receiver: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Wacom Bamboo
(II) LoadModule: "wacom"

(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) Wacom driver level: 47-0.8.1-4 $
(**) Wacom Bamboo: always reports core events
(**) Wacom Bamboo device is /dev/input/event8
(**) Wacom Bamboo is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) Wacom Bamboo: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Bamboo" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/event8"
Wacom Bamboo Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 30 for button 1
(==) Wacom USB Bamboo tablet speed=9600 (38400) maxX=14760 maxY=9225 maxZ=511 resX=2540 resY=2540  tilt=disabled
(==) Wacom device "Wacom Bamboo" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Composite USB PS2 Converter USB to PS2 Adaptor  V3.10
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: always reports core events
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Device: "/dev/input/event3"
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found x and y relative axes
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found 10 mouse buttons
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found keys
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Configuring as mouse
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Configuring as keyboard
(II) XINPUT: Adding extended input device "Composite USB PS2 Converter USB to PS2 Adaptor  V3.10" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_layout: "us"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: YAxisMapping: buttons 4 and 5
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Composite USB PS2 Converter USB to PS2 Adaptor  V3.10
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: always reports core events
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Device: "/dev/input/event2"
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found keys
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Configuring as keyboard
(II) XINPUT: Adding extended input device "Composite USB PS2 Converter USB to PS2 Adaptor  V3.10" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_layout: "us"
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: stoped with 1 channels, 48000 Hz sampling rate, 8 bits per sample,
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: 0x00 IEC60958 status bits and 0x00 category code
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling DACAEncoderControl
(II) RADEONHD(0): DACAEncoderControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
```

The only time the **/var/X11/Xorg.conf.0.log** even mentions 2048 and 1536 is here. Why is it saying "analog using initial mode 1152x864"!? And I set it prefer "2048x1536_85.00". 

```
(II) RADEONHD(0): Using fuzzy aspect match for initial modes
(II) RADEONHD(0): Output DVI-I_2/analog using initial mode 1152x864
(II) RADEONHD(0): RandR 1.2 support enabled
(==) RADEONHD(0): RGB weight 888
(==) RADEONHD(0): Default visual is TrueColor
(==) RADEONHD(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEONHD(0): Using 2048x1536 Framebuffer with 2048 pitch
(II) RADEONHD(0): FB: Allocated ScanoutBuffer at offset 0x00008000 (size = 0x00C00000)
(**) RADEONHD(0): Display dimensions: (406, 303) mm
(**) RADEONHD(0): DPI set to (128, 128)
```

**/etc/Xorg.conf**
```
Section	"Device"
	Identifier	"ATI Radeon HD4670"
	Driver		"radeonhd"
	Option		"AccelMethod" "exa"	# default shadowfb ; turn off if cause problems; experimental in HEAD radeonhd
	Option		"DRI" "on"		# turn off if cause problems; experimental in HEAD radeonhd
EndSection

Section	"Monitor"
	Identifier	"Sony GDM-F520"
	VendorName	"Sony"
	ModelName	"GDM-F520"
	HorizSync	30-137   					# units in kHz by default
	VertRefresh	48-170  					# units in Hz by default
	DisplaySize	406 303 					# specified in x y millimeters
	# Gamma		1.0						# specifies gamma
	# Gamma		1.0 1.0 1.0					# red green blue gammas
	UseModes	"Modes GDM-F520"				# make modes listed in Mode : modesection-id available for this monitor
	# Mode name							# provide definitions for video modes for monitor
		# DotClock	clock					# dot (pixel) clock rate to be used for mode
		# HTimings	hdisp hsyncstart hsyncend htotal	# horizontal timings for mode
		# VTimings	vdisp vsyncstart vcyncend vtotal	# vertical timings for mode
		# Flags		flag					# optional set of mode flags, each with a separate string in double-quotes
		# HSkew		hskew					# number of pixels towards right edge of screen by which display enable signal is to be skewed
		# VScan		vsacn					# number times each scanline is painted on the screen; 1 is default; DoubleScan Flag doubles this value
	# Option	TargetRefresh rate				# target vertical refresh rate when selecting video modes
	# Option	Position x y					# position of monitor within X screen
	# Option	LeftOf output					# monitor should be positioned to the left of the output (not monitor) of a given name
	# Option	MinClock 23.86					# minimum dot clock (kHz) supported by monitor
	# Option	MaxClock 388.04					# maximum dot clock (kHz) supported by monitor
	# Option	Rotate normal					# valid values normal, left, right, inverted
# 	Option		"PreferredMode" "2048x1536_85.00"		# specifies a mode to be marked as the preferred initial mode of the monitor
EndSection

Section	"Modes"
      Identifier	"Modes GDM-F520"
	#					Dotclock; hdisp, hsyncstart, hsyncend, htotal; vdisp, vsyncstart, vsyncend, vtotal
	# 9:5 ASPECT RATIO SETTINGS (slightly longer than 16:9)
	# Modlin 	"XxY_Refresh"		Dotclc	hdsp hsys hsye htot  vdsp vsys vsye vtot
	Modeline	"720x400_70.00"		26.15   720  736  808  896   400  401  404  417   -HSync +Vsync	# 720x400 @ 70.00 Hz (GTF) hsync: 29.19 kHz; pclk: 26.15 MHz
	Modeline	"720x400_85.00"		32.64   720  744  816  912   400  401  404  421   -HSync +Vsync	# 720x400 @ 85.00 Hz (GTF) hsync: 35.78 kHz; pclk: 32.64 MHz
	# 5:4 ASPECT RATIO SETTINGS
	# Modlin 	"XxY_Refresh"		Dotclc	hdsp hsys hsye htot  vdsp vsys vsye vtot
	Modeline	"1280x1024_60.00"	108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync	# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
	Modeline	"1280x1024_75.00"	138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync	# 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
	Modeline	"1280x1024_85.00"	159.36  1280 1376 1512 1744  1024 1025 1028 1075  -HSync +Vsync	# 1280x1024 @ 85.00 Hz (GTF) hsync: 91.38 kHz; pclk: 159.36 MHz
	# 4:3 ASPECT RATIO SETTINGS
	# Modlin 	"XxY_Refresh"		Dotclc	hdsp hsys hsye htot  vdsp vsys vsye vtot
	Modeline	"640x480_60.00"		23.86   640  656  720  800   480  481  484  497   -HSync +Vsync	# 640x480 @ 60.00 Hz (GTF) hsync: 29.82 kHz; pclk: 23.86 MHz
	Modeline	"640x480_75.00"		30.72   640  664  728  816   480  481  484  502   -HSync +Vsync	# 640x480 @ 75.00 Hz (GTF) hsync: 37.65 kHz; pclk: 30.72 MHz
	Modeline	"640x480_85.00"		35.71   640  672  736  832   480  481  484  505   -HSync +Vsync	# 640x480 @ 85.00 Hz (GTF) hsync: 42.92 kHz; pclk: 35.71 MHz
	Modeline	"800x600_60.00"		38.22   800  832  912  1024  600  601  604  622   -HSync +Vsync	# 800x600 @ 60.00 Hz (GTF) hsync: 37.32 kHz; pclk: 38.22 MHz
	Modeline	"800x600_75.00"		48.91   800  840  920  1040  600  601  604  627   -HSync +Vsync	# 800x600 @ 75.00 Hz (GTF) hsync: 47.03 kHz; pclk: 48.91 MHz
	Modeline	"800x600_85.00"		56.55   800  840  928  1056  600  601  604  630   -HSync +Vsync	# 800x600 @ 85.00 Hz (GTF) hsync: 53.55 kHz; pclk: 56.55 MHz
	Modeline	"832x624_75.00"		53.20   832  872  960  1088  624  625  628  652   -HSync +Vsync	# 832x624 @ 75.00 Hz (GTF) hsync: 48.90 kHz; pclk: 53.20 MHz
	Modeline	"1024x768_60.00"	64.11   1024 1080 1184 1344  768  769  772  795   -HSync +Vsync	# 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
	Modeline	"1024x768_70.00"	76.16   1024 1080 1192 1360  768  769  772  800   -HSync +Vsync	# 1024x768 @ 70.00 Hz (GTF) hsync: 56.00 kHz; pclk: 76.16 MHz
	Modeline	"1024x768_75.00"	81.80   1024 1080 1192 1360  768  769  772  802   -HSync +Vsync	# 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
	Modeline	"1024x768_85.00"	94.39   1024 1088 1200 1376  768  769  772  807   -HSync +Vsync	# 1024x768 @ 85.00 Hz (GTF) hsync: 68.60 kHz; pclk: 94.39 MHz
	Modeline	"1152x864_75.00"	104.99  1152 1224 1352 1552  864  865  868  902   -HSync +Vsync	# 1152x864 @ 75.00 Hz (GTF) hsync: 67.65 kHz; pclk: 104.99 MHz
	Modeline	"1152x864_85.00"	119.65  1152 1224 1352 1552  864  865  868  907   -HSync +Vsync	# 1152x864 @ 85.00 Hz (GTF) hsync: 77.10 kHz; pclk: 119.65 MHz
	Modeline	"1600x1200_60.00"	160.96  1600 1704 1880 2160  1200 1201 1204 1242  -HSync +Vsync	# 1600x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 160.96 MHz
	Modeline	"1600x1200_65.00"	176.23  1600 1712 1888 2176  1200 1201 1204 1246  -HSync +Vsync	# 1600x1200 @ 65.00 Hz (GTF) hsync: 80.99 kHz; pclk: 176.23 MHz
	Modeline	"1600x1200_70.00"	190.25  1600 1712 1888 2176  1200 1201 1204 1249  -HSync +Vsync	# 1600x1200 @ 70.00 Hz (GTF) hsync: 87.43 kHz; pclk: 190.25 MHz
	Modeline	"1600x1200_75.00"	205.99  1600 1720 1896 2192  1200 1201 1204 1253  -HSync +Vsync	# 1600x1200 @ 75.00 Hz (GTF) hsync: 93.97 kHz; pclk: 205.99 MHz
	Modeline	"1600x1200_85.00"	234.76  1600 1720 1896 2192  1200 1201 1204 1260  -HSync +Vsync	# 1600x1200 @ 85.00 Hz (GTF) hsync: 107.10 kHz; pclk: 234.76 MHz
	Modeline	"1920x1440_75.00"	297.59  1920 2072 2280 2640  1440 1441 1444 1503  -HSync +Vsync	# 1920x1440 @ 75.00 Hz (GTF) hsync: 112.73 kHz; pclk: 297.59 MHz
	Modeline	"1920x1440_85.00"	341.35  1920 2072 2288 2656  1440 1441 1444 1512  -HSync +Vsync	# 1920x1440 @ 85.00 Hz (GTF) hsync: 128.52 kHz; pclk: 341.35 MHz
	Modeline	"2048x1536_60.00"	266.95  2048 2200 2424 2800  1536 1537 1540 1589  -HSync +Vsync	# 2048x1536 @ 60.00 Hz (GTF) hsync: 95.34 kHz; pclk: 266.95 MHz
	Modeline	"2048x1536_75.00"	340.48  2048 2216 2440 2832  1536 1537 1540 1603  -HSync +Vsync	# 2048x1536 @ 75.00 Hz (GTF) hsync: 120.22 kHz; pclk: 340.48 MHz
	Modeline	"2048x1536_85.00"	388.04  2048 2216 2440 2832  1536 1537 1540 1612  -HSync +Vsync	# 2048x1536 @ 85.00 Hz (GTF) hsync: 137.02 kHz; pclk: 388.04 MHz
EndSection

Section	"Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon HD4670"
	Monitor		"Sony GDM-F520"
	DefaultDepth	24
	SubSection	"Display"
		Depth	24
		Modes	"2048x1536_75.00" "2048x1536_60.00" "1920x1440_85.00" "1920x1440_75.00" "1600x1200_85.00" "1600x1200_75.00" "1600x1200_65.00" "1600x1200_60.00" "1152x864_85.00" "1152x864_75.00" "1024x768_85.00" "1024x768_75.00" "1024x768_75.00" "1024x768_70.00" "1024x768_60.00" "832x624_75.00" "800x600_85.00" "800x600_75.00" "800x600_60.00" "640x480_85.00" "640x480_75.00" "640x480_60.00" "1280x1024_85.00" "1280x1024_75.00" "1280x1024_60.00" "720x400_85.00" "720x400_70.00"
		Virtual	2048 1536					# specifies the virtual screen resolution to be used; 5888 2400 for GDM-F520 + VP2290B
	EndSubSection
	SubSection	"Display"
		Depth	16
		Modes	"2048x1536_75.00" "2048x1536_60.00" "1920x1440_85.00" "1920x1440_75.00" "1600x1200_85.00" "1600x1200_75.00" "1600x1200_65.00" "1600x1200_60.00" "1152x864_85.00" "1152x864_75.00" "1024x768_85.00" "1024x768_75.00" "1024x768_75.00" "1024x768_70.00" "1024x768_60.00" "832x624_75.00" "800x600_85.00" "800x600_75.00" "800x600_60.00" "640x480_85.00" "640x480_75.00" "640x480_60.00" "1280x1024_85.00" "1280x1024_75.00" "1280x1024_60.00" "720x400_85.00" "720x400_70.00"
		Virtual	2048 1536					# specifies the virtual screen resolution to be used; 5888 2400 for GDM-F520 + VP2290B
	EndSubSection
	SubSection	"Display"
		Depth	8
		Modes	"2048x1536_75.00" "2048x1536_60.00" "1920x1440_85.00" "1920x1440_75.00" "1600x1200_85.00" "1600x1200_75.00" "1600x1200_65.00" "1600x1200_60.00" "1152x864_85.00" "1152x864_75.00" "1024x768_85.00" "1024x768_75.00" "1024x768_75.00" "1024x768_70.00" "1024x768_60.00" "832x624_75.00" "800x600_85.00" "800x600_75.00" "800x600_60.00" "640x480_85.00" "640x480_75.00" "640x480_60.00" "1280x1024_85.00" "1280x1024_75.00" "1280x1024_60.00" "720x400_85.00" "720x400_70.00"
		Virtual	2048 1536					# specifies the virtual screen resolution to be used; 5888 2400 for GDM-F520 + VP2290B
	EndSubSection
EndSection
```

And lastly, the output of xrandr and using xrandr --addmode. 

output of typing **xrandr**
```
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 2048 x 1536
DVI-I_1/digital disconnected (normal left inverted right x axis y axis)
DVI-I_1/analog disconnected (normal left inverted right x axis y axis)
DVI-I_2/digital disconnected (normal left inverted right x axis y axis)
DVI-I_2/analog connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8
   1152x864       60.0*
   1024x768       60.0
   800x600        60.3
   640x480        59.9
  2048x1536_85.00 (0xa5)  388.0MHz
        h: width  2048 start 2216 end 2440 total 2832 skew    0 clock  137.0KHz
        v: height 1536 start 1537 end 1540 total 1612           clock   85.0Hz
```

Result of typing **xrandr --addmode DVI-I_2/analog 2048x1536_85.00**
```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  18 ()
  Serial number of failed request:  17
  Current serial number in output stream:  18
```

---

### Post by Favux on 2009-03-21
Hi dh003i,

I'm sorry, I don't know much about video stuff.  Hopefully someone who knows more will answer shortly.  But don't you need a "ServerLayout" section at the end of your xorg.conf?  Something like:
```
Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen 		"Default Screen"
EndSection
```

---

### Post by dh003i on 2009-03-22
Now, I've added the following to my xorg.conf file, and it still doesn't work:

**xorg.conf (additions from above post)**
```

Section	"Serverflags"
	Option 		"DefaultServerLayout" "DefaultLayout"	# specifies the default ServerLayout section to use in the absence of the -layout command line option.
Endsection

Section	"ServerLayout"
	Identifier	"DefaultLayout"
	Screen		1 "Default Screen" 0 0
Endsection
```

Btw, my latest **/var/log/Xorg.0.log** output (with the ModeDebug "True" setting in my xorg.conf for more debugging info):
```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux davidjheinrich 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Mar 22 02:40:30 2009
(==) Using config file: "/etc/X11/xorg.conf"
(**) Option "defaultserverlayout" "DefaultLayout"
(**) ServerLayout "DefaultLayout"
(**) |-->Screen "Default Screen" (1)
(**) |   |-->Monitor "Sony GDM-F520"
(**) |   |-->Device "ATI Radeon HD4670"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7b7320
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0@1:0:0) ATI Technologies Inc RV730XT [Radeon HD 4670] rev 0, Mem @ 0xd0000000/268435456, 0xfe8e0000/65536, I/O @ 0x0000b000/256, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
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
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "radeonhd"

(II) Loading /usr/lib/xorg/modules/drivers//radeonhd_drv.so
(II) Module radeonhd: vendor="AMD GPG"
	compiled for 1.5.2, module version = 1.2.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) RADEONHD: X driver for the following AMD GPG (ATI) graphics devices:
	RV505 : Radeon X1550, X1550 64bit.
	RV515 : Radeon X1300, X1550, X1600; FireGL V3300, V3350.
	RV516 : Radeon X1300, X1550, X1550 64-bit, X1600; FireMV 2250.
	R520  : Radeon X1800; FireGL V5300, V7200, V7300, V7350.
	RV530 : Radeon X1300 XT, X1600, X1600 Pro, X1650; FireGL V3400, V5200.
	RV535 : Radeon X1300, X1650.
	RV550 : Radeon X2300 HD.
	RV560 : Radeon X1650.
	RV570 : Radeon X1950, X1950 GT; FireGL V7400.
	R580  : Radeon X1900, X1950; AMD Stream Processor.
	R600  : Radeon HD 2900 GT/Pro/XT; FireGL V7600/V8600/V8650.
	RV610 : Radeon HD 2350, HD 2400 Pro/XT, HD 2400 Pro AGP; FireGL V4000.
	RV620 : Radeon HD 3450, HD 3470.
	RV630 : Radeon HD 2600 LE/Pro/XT, HD 2600 Pro/XT AGP; Gemini RV630;
		FireGL V3600/V5600.
	RV635 : Radeon HD 3650, HD 3670.
	RV670 : Radeon HD 3690, 3850, HD 3870, FireGL V7700, FireStream 9170.
	R680  : Radeon HD 3870 X2.
	M52   : Mobility Radeon X1300.
	M54   : Mobility Radeon X1400; M54-GL.
	M56   : Mobility Radeon X1600; Mobility FireGL V5200.
	M58   : Mobility Radeon X1800, X1800 XT; Mobility FireGL V7100, V7200.
	M62   : Mobility Radeon X1350.
	M64   : Mobility Radeon X1450, X2300.
	M66   : Mobility Radeon X1700, X1700 XT; FireGL V5250.
	M68   : Mobility Radeon X1900.
	M71   : Mobility Radeon HD 2300.
	M72   : Mobility Radeon HD 2400; Radeon E2400.
	M74   : Mobility Radeon HD 2400 XT.
	M76   : Mobility Radeon HD 2600;
		(Gemini ATI) Mobility Radeon HD 2600 XT.
	M82   : Mobility Radeon HD 3400.
	M86   : Mobility Radeon HD 3650, HD 3670, Mobility FireGL V5700.
	M88   : Mobility Radeon HD 3850, HD 3850 X2, HD 3870, HD3870 X2.
	RS600 : Radeon Xpress 1200, Xpress 1250.
	RS690 : Radeon X1200, X1250, X1270.
	RS740 : RS740, RS740M.
	RS780 : Radeon HD 3100/3200/3300 Series.
	RV770 : Radeon HD 4800 Series; Everest, K2, Denali ATI FirePro.
	R700  : Radeon R700.
	M98   : Radeon M98 Mobility.
	RV730 : Radeon HD4670, HD4650.
	M96   : Radeon M96 Mobility.
	RV710 : Radeon HD4570, HD4350.

(II) RADEONHD: version 1.2.4, built from git branch master, commit d9c8f9ce

(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) RADEONHD(0): Depth 24, (--) framebuffer bpp 32
(**) RADEONHD(0): Option "AccelMethod" "exa"
(**) RADEONHD(0): Option "DRI" "on"
(**) RADEONHD(0): Selected EXA 2D acceleration.
(II) RADEONHD(0): Unknown card detected: 0x9490:0x1462:0x1590.
	If - and only if - your card does not work or does not work optimally
	please contact radeonhd@opensuse.org to help rectify this.
	Use the subject: 0x9490:0x1462:0x1590: <name of board>
	and *please* describe the problems you are seeing
	in your message.
(--) RADEONHD(0): Detected an RV730 on an unidentified card
(II) RADEONHD(0): Mapped IO @ 0xfe8e0000 to 0x7f23b3c96000 (size 0x00010000)
(II) RADEONHD(0): PCIE Card Detected
(II) RADEONHD(0): Getting BIOS copy from legacy VBIOS location
(II) RADEONHD(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1462 SubsystemID: 0x1590
	IOBaseAddress: 0xb000
	Filename: Test.bin    
	BIOS Bootup Message: 
113-MSITV159MS.100-AB73100-100-MI RV730 GDDR3 128BIT 750E/1000M               
(II) RADEONHD(0): Analog TV Default Mode: 1
(II) RADEONHD(0): Found default TV Mode NTSC
(II) RADEONHD(0): The detected amount of videoram exceeds the PCI BAR aperture.
(II) RADEONHD(0): Using only 262144kB of the total 524288kB.
(--) RADEONHD(0): VideoRAM: 262144 kByte
(II) RADEONHD(0): Framebuffer space used by Firmware (kb): 20
(II) RADEONHD(0): Start of VRAM area used by Firmware: 0x7ffec
(II) RADEONHD(0): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEONHD(0): AtomBIOS VRAM scratch base: 0x7ffec
(WW) RADEONHD(0): rhdAtomAllocateFbScratch: FW FB scratch area not located at the end of VRAM. Scratch End: 0x84fec VRAM End: 0x10000000
(II) RADEONHD(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEONHD(0): Default Engine Clock: 750000
(II) RADEONHD(0): Default Memory Clock: 1000000
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Input: 16000
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Input: 6000
(II) RADEONHD(0): Maximum Pixel Clock: 400000
(II) RADEONHD(0): Reference Clock: 27000
(WW) RADEONHD(0): Direct rendering for R600 and up forced on - This is NOT officially supported yet and may cause instability or lockups
(II) RADEONHD(0): Found libdri 5.4.0.
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEONHD(0): Found libdrm 1.3.0.
(II) RADEONHD(0): Found radeon drm 1.29.0.
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEONHD(0): Reference Clock: 27000
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f90
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f90
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 0" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f94
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f94
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 1" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f98
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f98
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 2" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f88
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f88
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 3" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1fc4
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1fc4
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 4" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1fe8
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1fe8
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 5" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) RADEONHD(0): Detected VGA mode.
(**) RADEONHD(0): Using AtomBIOS for Crtcs
(**) RADEONHD(0): Using AtomBIOS for PLLs
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEONHD(0): Maximum Pixel Clock: 400000
(II) RADEONHD(0): Reference Clock: 27000
(II) RADEONHD(0): rhdAtomSetPixelClockVersion returned version 3 for index 0xc
(II) RADEONHD(0): rhdAtomSetPixelClockVersion returned version 3 for index 0xc
(II) RADEONHD(0): FB: Allocated Cursor Image at offset 0x00000000 (size = 0x00004000)
(II) RADEONHD(0): FB: Allocated Cursor Image at offset 0x00004000 (size = 0x00004000)
(II) RADEONHD(0): Connector[0] {RHD_CONNECTOR_DVI, "DUAL_LINK_DVI_I CRT2 DFP2", RHD_DDC_4, RHD_HPD_1, { RHD_OUTPUT_UNIPHYC, RHD_OUTPUT_DACB } }
(II) RADEONHD(0): Connector[1] {RHD_CONNECTOR_DVI, "DUAL_LINK_DVI_I CRT1 DFP1", RHD_DDC_3, RHD_HPD_0, { RHD_OUTPUT_UNIPHYA, RHD_OUTPUT_DACA } }
(**) RADEONHD(0): Using AtomBIOS for Outputs
(EE) RADEONHD(0): RHDHdmiInit: unknown HDMI output type
(II) RADEONHD(0): rhdAtomSelectCrtcSourceVersion returned version 2 for index 0x2a
(--) RADEONHD(0): Attaching Output AtomOutputUniphyC to Connector DVI-I 1
(**) RADEONHD(0): Using AtomBIOS for Outputs
(II) RADEONHD(0): rhdAtomSelectCrtcSourceVersion returned version 2 for index 0x2a
(--) RADEONHD(0): Attaching Output AtomOutputDACB to Connector DVI-I 1
(**) RADEONHD(0): Using AtomBIOS for Outputs
(II) RADEONHD(0): rhdAtomSelectCrtcSourceVersion returned version 2 for index 0x2a
(--) RADEONHD(0): Attaching Output AtomOutputUniphyA to Connector DVI-I 2
(**) RADEONHD(0): Using AtomBIOS for Outputs
(II) RADEONHD(0): rhdAtomSelectCrtcSourceVersion returned version 2 for index 0x2a
(--) RADEONHD(0): Attaching Output AtomOutputDACA to Connector DVI-I 2
(II) RADEONHD(0): RandR: Adding RRoutput DVI-I_1/digital for Output AtomOutputUniphyC
(II) RADEONHD(0): RandR: Adding RRoutput DVI-I_1/analog for Output AtomOutputDACB
(II) RADEONHD(0): RandR: Adding RRoutput DVI-I_2/digital for Output AtomOutputUniphyA
(II) RADEONHD(0): RandR: Adding RRoutput DVI-I_2/analog for Output AtomOutputDACA
(II) RADEONHD(0): Output DVI-I_1/digital using monitor section Sony GDM-F520
(II) RADEONHD(0): Output DVI-I_1/digital has no monitor section
(II) RADEONHD(0): Output DVI-I_1/analog has no monitor section
(II) RADEONHD(0): Output DVI-I_2/digital has no monitor section
(II) RADEONHD(0): Output DVI-I_2/analog has no monitor section
(**) RADEONHD(0): Option "ModeDebug" "True"
(II) RADEONHD(0): EDID for output DVI-I_1/digital
(II) RADEONHD(0): EDID for output DVI-I_1/analog
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: none
(II) RADEONHD(0): EDID for output DVI-I_2/digital
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Setting AtomOutputDACA to incoherent
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): EDID for output DVI-I_2/analog
(II) RADEONHD(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x175" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "360x200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEONHD(0): Not using default mode "640x480" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEONHD(0): Not using default mode "640x512" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x512" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x512" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEONHD(0): Not using default mode "800x600" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEONHD(0): Not using default mode "896x672" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "896x672" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEONHD(0): Not using default mode "928x696" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "928x696" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x720" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "960x720" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "416x312" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEONHD(0): Not using default mode "680x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "680x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "700x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1440x900" (hsync out of range)
(II) RADEONHD(0): Not using default mode "720x450" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1600x1024" (hsync out of range)
(II) RADEONHD(0): Not using default mode "800x512" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "840x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "840x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1920x1080" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x540" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x600" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "960x720" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Printing probed modes for output DVI-I_2/analog
(II) RADEONHD(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEONHD(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEONHD(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEONHD(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEONHD(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEONHD(0): Output DVI-I_1/digital disconnected
(II) RADEONHD(0): Output DVI-I_1/analog disconnected
(II) RADEONHD(0): Output DVI-I_2/digital disconnected
(II) RADEONHD(0): Output DVI-I_2/analog connected
(II) RADEONHD(0): Using fuzzy aspect match for initial modes
(II) RADEONHD(0): Output DVI-I_2/analog using initial mode 1152x864
(II) RADEONHD(0): RandR 1.2 support enabled
(==) RADEONHD(0): RGB weight 888
(==) RADEONHD(0): Default visual is TrueColor
(==) RADEONHD(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEONHD(0): Using 2048x1536 Framebuffer with 2048 pitch
(II) RADEONHD(0): FB: Allocated ScanoutBuffer at offset 0x00008000 (size = 0x00C00000)
(**) RADEONHD(0): Display dimensions: (406, 303) mm
(**) RADEONHD(0): DPI set to (128, 128)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "exa"
(II) LoadModule: "exa"

(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEONHD(0): FB: Allocated Offscreen Buffer at offset 0x00C08000 (size = 0x01998000)
(II) RADEONHD(0): FB: Allocated DRI Back Buffer at offset 0x025A0000 (size = 0x00C00000)
(II) RADEONHD(0): FB: Allocated DRI Depth Buffer at offset 0x031A0000 (size = 0x00C00000)
(II) RADEONHD(0): FB: Allocated GART table at offset 0x0FFF0000 (size = 0x00010000, end of FB)
(II) RADEONHD(0): FB: Allocated DRI Textures at offset 0x03DA0000 (size = 0x0C000000)
(II) RADEONHD(0): Using 16 MB GART aperture
(II) RADEONHD(0): Using 2 MB for the ring buffer
(II) RADEONHD(0): Using 2 MB for vertex/indirect buffers
(II) RADEONHD(0): Using 12 MB for GART textures
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) RADEONHD(0): Mapped IO @ 0xfe8e0000 to 0x7f23b3c96000 (size 0x00010000)
(II) RADEONHD(0): Mapped FB @ 0xd0000000 to 0x7f239fff7000 (size 0x10000000)
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEONHD(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEONHD(0): [drm] framebuffer handle = 0xd0000000
(II) RADEONHD(0): [drm] added 1 reserved context for kernel
(II) RADEONHD(0): X context handle = 0x1
(II) RADEONHD(0): [drm] installed DRM signal handler
(II) RADEONHD(0): [pci] 16384 kB allocated with handle 0x1258d200
(II) RADEONHD(0): [pci] ring handle = 0x1effe000
(II) RADEONHD(0): [pci] Ring mapped at 0x7f239fdf6000
(II) RADEONHD(0): [pci] Ring contents 0x00000000
(II) RADEONHD(0): [pci] ring read ptr handle = 0x2effe000
(II) RADEONHD(0): [pci] Ring read ptr mapped at 0x7f23b3c4b000
(II) RADEONHD(0): [pci] Ring read ptr contents 0x00000000
(II) RADEONHD(0): [pci] vertex/indirect buffers handle = 0x1f000000
(II) RADEONHD(0): [pci] Vertex/indirect buffers mapped at 0x7f239fbf6000
(II) RADEONHD(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEONHD(0): [pci] GART texture map handle = 0x1f001000
(II) RADEONHD(0): [pci] GART Texture map mapped at 0x7f239f036000
(II) RADEONHD(0): [drm] register handle = 0xfe8e0000
(II) RADEONHD(0): [dri] Visual configs initialized
(II) RADEONHD(0): [DRI] installation complete
(II) RADEONHD(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEONHD(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEONHD(0): [drm] dma control initialized, using IRQ 16
(II) RADEONHD(0): [drm] Initialized kernel GART heap manager, 12320768
(II) RADEONHD(0): Direct rendering enabled
(II) RADEONHD(0): Using DRM Command Processor (indirect) for acceleration.
(II) EXA(0): Offscreen pixmap area of 26836992 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II)         DownloadFromScreen
(==) RADEONHD(0): Backing store disabled
(==) RADEONHD(0): Silken mouse enabled
(II) RADEONHD(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling DAC2OutputControl
(II) RADEONHD(0): DAC2OutputControl Successful
(II) RADEONHD(0): Calling DACBEncoderControl
(II) RADEONHD(0): DACBEncoderControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling DACAEncoderControl
(II) RADEONHD(0): DACAEncoderControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): On Crtc 0 Setting 60.0 Hz Mode: Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync
(II) RADEONHD(0): Calling SetCRTC_Timing
(II) RADEONHD(0): SetCRTC_Timing Successful
(II) RADEONHD(0): CallingSetCRTC_OverScan
(II) RADEONHD(0): Set CRTC_OverScan Successful
(II) RADEONHD(0): Calling EnableScaler
(II) RADEONHD(0): EnableScaler Successful
(II) RADEONHD(0): Calling SetPixelClock
(II) RADEONHD(0): SetPixelClock Successful
(II) RADEONHD(0): Calling SelectCRTCSource
(II) RADEONHD(0): SelectCRTCSource Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling DACAEncoderControl
(II) RADEONHD(0): DACAEncoderControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling DAC2OutputControl
(II) RADEONHD(0): DAC2OutputControl Successful
(II) RADEONHD(0): Calling DACBEncoderControl
(II) RADEONHD(0): DACBEncoderControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): RHDAudioSetSupported: config 0x60040 codec 0x1
(II) RADEONHD(0): DPMS enabled
(II) RADEONHD(0): Xv: Textured Video initialised.
(WW) RADEONHD(0): Option "DVI-I_2/analog" is not used
(--) RandR disabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(EE) AIGLX error: dlopen of /usr/lib/dri/r600_dri.so failed (/usr/lib/dri/r600_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) RADEONHD(0): Setting screen physical size to 304 x 228
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found 1 mouse buttons
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found 16 mouse buttons
(II) Logitech USB Receiver: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Wacom Bamboo
(II) LoadModule: "wacom"

(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) Wacom driver level: 47-0.8.1-4 $
(**) Wacom Bamboo: always reports core events
(**) Wacom Bamboo device is /dev/input/event8
(**) Wacom Bamboo is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) Wacom Bamboo: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Bamboo" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/event8"
Wacom Bamboo Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 30 for button 1
(==) Wacom USB Bamboo tablet speed=9600 (38400) maxX=14760 maxY=9225 maxZ=511 resX=2540 resY=2540  tilt=disabled
(==) Wacom device "Wacom Bamboo" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Composite USB PS2 Converter USB to PS2 Adaptor  V3.10
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: always reports core events
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Device: "/dev/input/event3"
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found x and y relative axes
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found 10 mouse buttons
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found keys
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Configuring as mouse
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Configuring as keyboard
(II) XINPUT: Adding extended input device "Composite USB PS2 Converter USB to PS2 Adaptor  V3.10" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_layout: "us"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: YAxisMapping: buttons 4 and 5
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Composite USB PS2 Converter USB to PS2 Adaptor  V3.10
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: always reports core events
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Device: "/dev/input/event2"
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found keys
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Configuring as keyboard
(II) XINPUT: Adding extended input device "Composite USB PS2 Converter USB to PS2 Adaptor  V3.10" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_layout: "us"
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: stoped with 1 channels, 48000 Hz sampling rate, 8 bits per sample,
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: 0x00 IEC60958 status bits and 0x00 category code
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
AUDIT: Sun Mar 22 02:40:33 2009: 8528 X: client 16 rejected from local host ( uid=1000 gid=1000 pid=8929 )
AUDIT: Sun Mar 22 02:40:33 2009: 8528 X: client 16 rejected from local host ( uid=1000 gid=1000 pid=8931 )
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): EDID for output DVI-I_1/digital
(II) RADEONHD(0): EDID for output DVI-I_1/analog
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): EDID for output DVI-I_2/digital
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): EDID for output DVI-I_2/analog
(II) RADEONHD(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x175" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "360x200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEONHD(0): Not using default mode "640x480" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEONHD(0): Not using default mode "640x512" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x512" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x512" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEONHD(0): Not using default mode "800x600" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEONHD(0): Not using default mode "896x672" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "896x672" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEONHD(0): Not using default mode "928x696" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "928x696" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x720" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "960x720" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "416x312" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEONHD(0): Not using default mode "680x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "680x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "700x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1440x900" (hsync out of range)
(II) RADEONHD(0): Not using default mode "720x450" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1600x1024" (hsync out of range)
(II) RADEONHD(0): Not using default mode "800x512" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "840x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "840x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1920x1080" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x540" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x600" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "960x720" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Printing probed modes for output DVI-I_2/analog
(II) RADEONHD(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEONHD(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEONHD(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEONHD(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEONHD(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEONHD(0): EDID for output DVI-I_1/digital
(II) RADEONHD(0): EDID for output DVI-I_1/analog
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): EDID for output DVI-I_2/digital
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): EDID for output DVI-I_2/analog
(II) RADEONHD(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x175" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "360x200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEONHD(0): Not using default mode "640x480" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEONHD(0): Not using default mode "640x512" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x512" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x512" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEONHD(0): Not using default mode "800x600" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEONHD(0): Not using default mode "896x672" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "896x672" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEONHD(0): Not using default mode "928x696" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "928x696" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x720" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "960x720" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "416x312" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEONHD(0): Not using default mode "680x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "680x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "700x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1440x900" (hsync out of range)
(II) RADEONHD(0): Not using default mode "720x450" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1600x1024" (hsync out of range)
(II) RADEONHD(0): Not using default mode "800x512" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "840x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "840x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1920x1080" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x540" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x600" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "960x720" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Printing probed modes for output DVI-I_2/analog
(II) RADEONHD(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEONHD(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEONHD(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEONHD(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEONHD(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEONHD(0): EDID for output DVI-I_1/digital
(II) RADEONHD(0): EDID for output DVI-I_1/analog
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): EDID for output DVI-I_2/digital
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): EDID for output DVI-I_2/analog
(II) RADEONHD(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x175" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "360x200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEONHD(0): Not using default mode "640x480" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEONHD(0): Not using default mode "640x512" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x512" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x512" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEONHD(0): Not using default mode "800x600" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEONHD(0): Not using default mode "896x672" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "896x672" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEONHD(0): Not using default mode "928x696" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "928x696" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x720" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "960x720" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "416x312" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEONHD(0): Not using default mode "680x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "680x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "700x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1440x900" (hsync out of range)
(II) RADEONHD(0): Not using default mode "720x450" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1600x1024" (hsync out of range)
(II) RADEONHD(0): Not using default mode "800x512" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "840x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "840x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1920x1080" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x540" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x600" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "960x720" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Printing probed modes for output DVI-I_2/analog
(II) RADEONHD(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEONHD(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEONHD(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEONHD(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEONHD(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEONHD(0): EDID for output DVI-I_1/digital
(II) RADEONHD(0): EDID for output DVI-I_1/analog
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): EDID for output DVI-I_2/digital
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): EDID for output DVI-I_2/analog
(II) RADEONHD(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x175" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "360x200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEONHD(0): Not using default mode "640x480" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEONHD(0): Not using default mode "640x512" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x512" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x512" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEONHD(0): Not using default mode "800x600" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEONHD(0): Not using default mode "896x672" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "896x672" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEONHD(0): Not using default mode "928x696" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "928x696" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x720" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "960x720" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "416x312" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEONHD(0): Not using default mode "680x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "680x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "700x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1440x900" (hsync out of range)
(II) RADEONHD(0): Not using default mode "720x450" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1600x1024" (hsync out of range)
(II) RADEONHD(0): Not using default mode "800x512" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "840x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "840x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1920x1080" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x540" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x600" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "960x720" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Printing probed modes for output DVI-I_2/analog
(II) RADEONHD(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEONHD(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEONHD(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEONHD(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEONHD(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling DACAEncoderControl
(II) RADEONHD(0): DACAEncoderControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): EDID for output DVI-I_1/digital
(II) RADEONHD(0): EDID for output DVI-I_1/analog
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): EDID for output DVI-I_2/digital
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): EDID for output DVI-I_2/analog
(II) RADEONHD(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x175" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "360x200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEONHD(0): Not using default mode "640x480" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEONHD(0): Not using default mode "640x512" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x512" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x512" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEONHD(0): Not using default mode "800x600" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEONHD(0): Not using default mode "896x672" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "896x672" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEONHD(0): Not using default mode "928x696" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "928x696" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x720" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "960x720" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "416x312" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEONHD(0): Not using default mode "680x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "680x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "700x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1440x900" (hsync out of range)
(II) RADEONHD(0): Not using default mode "720x450" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1600x1024" (hsync out of range)
(II) RADEONHD(0): Not using default mode "800x512" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "840x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "840x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1920x1080" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x540" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x600" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "960x720" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Printing probed modes for output DVI-I_2/analog
(II) RADEONHD(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEONHD(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEONHD(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEONHD(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEONHD(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEONHD(0): EDID for output DVI-I_1/digital
(II) RADEONHD(0): EDID for output DVI-I_1/analog
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): EDID for output DVI-I_2/digital
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" removed.
(II) RADEONHD(0): EDID for output DVI-I_2/analog
(II) RADEONHD(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x175" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "360x200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEONHD(0): Not using default mode "640x480" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEONHD(0): Not using default mode "640x512" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x512" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x512" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEONHD(0): Not using default mode "800x600" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEONHD(0): Not using default mode "896x672" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "896x672" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEONHD(0): Not using default mode "928x696" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "928x696" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x720" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "960x720" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "416x312" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEONHD(0): Not using default mode "680x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "680x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "700x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1440x900" (hsync out of range)
(II) RADEONHD(0): Not using default mode "720x450" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1600x1024" (hsync out of range)
(II) RADEONHD(0): Not using default mode "800x512" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "840x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "840x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1920x1080" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x540" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x600" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "960x720" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Printing probed modes for output DVI-I_2/analog
(II) RADEONHD(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEONHD(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEONHD(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEONHD(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEONHD(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
```

---

### Post by dh003i on 2009-03-22
One thing that I noticed in particular in the **/var/log/Xorg.0.log** file is this. What's all this stuff about not using the default modes I specified, vrefresh out of range, hsync out of range, and doublescan not supported? (am I specifying something incorrectly here?)
```
(II) RADEONHD(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x175" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "360x200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "320x240" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEONHD(0): Not using default mode "640x480" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEONHD(0): Not using default mode "640x512" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x512" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "640x512" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEONHD(0): Not using default mode "800x600" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEONHD(0): Not using default mode "896x672" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "896x672" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEONHD(0): Not using default mode "928x696" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "928x696" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x720" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "960x720" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "416x312" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "576x432" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) RADEONHD(0): Not using default mode "680x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "680x384" (doublescan mode not supported)
(II) RADEONHD(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "700x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "700x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1440x900" (hsync out of range)
(II) RADEONHD(0): Not using default mode "720x450" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1600x1024" (hsync out of range)
(II) RADEONHD(0): Not using default mode "800x512" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "840x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEONHD(0): Not using default mode "840x525" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "840x525" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1920x1080" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x540" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEONHD(0): Not using default mode "960x600" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "960x720" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) RADEONHD(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEONHD(0): Printing probed modes for output DVI-I_2/analog
(II) RADEONHD(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEONHD(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) RADEONHD(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEONHD(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEONHD(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
```

---

### Post by Favux on 2009-03-22
Hi again dh003i,

Again with the disclaimer that with video stuff I don't know what I'm talking about I'm wondering about:
```
Section	"Modes"
      Identifier	"Modes GDM-F520"
	#					Dotclock; hdisp, hsyncstart, hsyncend, htotal; vdisp, vsyncstart, vsyncend, vtotal
	# 9:5 ASPECT RATIO SETTINGS (slightly longer than 16:9)
	# Modlin 	"XxY_Refresh"		Dotclc	hdsp hsys hsye htot  vdsp vsys vsye vtot
	Modeline	"720x400_70.00"		26.15   720  736  808  896   400  401  404  417   -HSync +Vsync	# 720x400 @ 70.00 Hz (GTF) hsync: 29.19 kHz; pclk: 26.15 MHz
	Modeline	"720x400_85.00"		32.64   720  744  816  912   400  401  404  421   -HSync +Vsync	# 720x400 @ 85.00 Hz (GTF) hsync: 35.78 kHz; pclk: 32.64 MHz
etc.
EndSection

```
Aren't the modes usually in the:
```
Section	"Screen"

```
like some you already have?  And I think maybe I'll shut up.

---

### Post by dh003i on 2009-03-22
Hi Favux,

> Aren't the modes usually in the:
```
Section	"Screen"

```
like some you already have?  And I think maybe I'll shut up.

I tried that too, putting the modelines directly in the **Section "Display"** (I think that's what you meant, the Screen section binds together Display and Device sections). It doesn't improve matters. 

So I reverted back to separating them out. The modelines can be referenced from the Display section by using "UseModes modesection-id", which refers to the Identifier text in the **Section "Modes"**.

---

### Post by dh003i on 2009-03-22
Ok, now I have 2048x1536, but not through any xorg.conf settings, through xrandr manipulation (but this is annoying, as I don't want to do this every time):

Here's what I did to get 2048x1536 @ 60Hz (where ~$ represents my prompt):
```
**~$ gtf 2048 1536 60**

  # 2048x1536 @ 60.00 Hz (GTF) hsync: 95.34 kHz; pclk: 266.95 MHz
  Modeline "2048x1536_60.00"  266.95  2048 2200 2424 2800  1536 1537 1540 1589  -HSync +Vsync

**~$ xrandr --newmode "2048x1536_60.00"  267.25  2048 2208 2424 2800  1536 1539 1543 1592 -hsync +vsy**

**~$ xrandr --addmode DVI-I_2/analog 2048x1536_60.00**

**~$ xrandr**
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 2048 x 1536
DVI-I_1/digital disconnected (normal left inverted right x axis y axis)
DVI-I_1/analog disconnected (normal left inverted right x axis y axis)
DVI-I_2/digital disconnected (normal left inverted right x axis y axis)
DVI-I_2/analog connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8
   1152x864       60.0*
   1024x768       60.0
   800x600        60.3
   640x480        59.9
   2048x1536_60.00   60.0
```

PS: Doing the exact same thing, but for 2048 x 1536 @ 75.00 Hz (with he appropriate gtf-generated modeline, doesn't work). Anything about 73.00 Hz generates a similar error. Huh? This CRT's manual says it supports 2048x1536 at at least 85 Hz, and a very reputable Sony-tech / eBay seller of these monitors (Unkle Vito) e-mailed me that it supports 2048x1536 @ 120 Hz (although he wouldn't recommend above 85 Hz). Also, even though it works for refresh rates of up to 73 Hz, I can't select hose from the "Configure Display" widget in KDE (it allows me to pull down 73 or 70, but then when I click Apply or OK, it goes back to "Auto" or 60Hz). 

```
**~# gtf 2048 1536 75**

  # 2048x1536 @ 75.00 Hz (GTF) hsync: 120.22 kHz; pclk: 340.48 MHz
  Modeline "2048x1536_75.00"  340.48  2048 2216 2440 2832  1536 1537 1540 1603  -HSync +Vsync

**~# xrandr --newmode "2048x1536_75.00"  340.48  2048 2216 2440 2832  1536 1537 1540 1603  -HSync +Vsync**

**~# xrandr --addmode DVI-I_2/analog 2048x1536_75.00**
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  18 ()
  Serial number of failed request:  17
  Current serial number in output stream:  18

**~# xrandr**
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 2048 x 1536
DVI-I_1/digital disconnected (normal left inverted right x axis y axis)
DVI-I_1/analog disconnected (normal left inverted right x axis y axis)
DVI-I_2/digital disconnected (normal left inverted right x axis y axis)
DVI-I_2/analog connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8
   1152x864       60.0*
   1024x768       60.0
   800x600        60.3
   640x480        59.9
  2048x1536_75.00 (0x99)  340.5MHz
        h: width  2048 start 2216 end 2440 total 2832 skew    0 clock  120.2KHz
        v: height 1536 start 1537 end 1540 total 1603           clock   75.0Hz

```

---

### Post by ebharv on 2009-03-24
Regarding the post with all the hsync and vrefresh out of range, I think it's telling that your vertical refresh rates are not supported. Have you tried removing the refresh rates from your resolution modes in your "Display" SubSections. ("2048x1536" instead of "2048x1536_75.00").

In the meantime have you tried doing this ```
(II) RADEONHD(0): Unknown card detected: 0x9490:0x1462:0x1590. 
 If - and only if - your card does not work or does not work optimally	please contact radeonhd@opensuse.org to help rectify this.	Use the subject: 0x9490:0x1462:0x1590: <name of board>	and *please* describe the problems you are seeing	in your message.
```

I'm very intrested in your problem as I plan to build my next system using AMD's Dragon platform.

---

### Post by dh003i on 2009-03-24
> **ebharv said:**
> Regarding the post with all the hsync and vrefresh out of range, I think it's telling that your vertical refresh rates are not supported. Have you tried removing the refresh rates from your resolution modes in your "Display" SubSections. ("2048x1536" instead of "2048x1536_75.00").

In the meantime have you tried doing this ```
(II) RADEONHD(0): Unknown card detected: 0x9490:0x1462:0x1590. 
 If - and only if - your card does not work or does not work optimally	please contact radeonhd@opensuse.org to help rectify this.	Use the subject: 0x9490:0x1462:0x1590: <name of board>	and *please* describe the problems you are seeing	in your message.
```

I'm very intrested in your problem as I plan to build my next system using AMD's Dragon platform.

What's AMD Dragon?

Btw, The "2048x1536_75.00" is just the name of that resolution specification; it doesn't actually specify anything. I.e., in the following modeline:

```

# Modlin 	"XxY_Refresh"		Dotclc	hdsp hsys hsye htot  vdsp vsys vsye vtot
Modeline	"2048x1500_60.00"	260.74  2048 2200 2424 2800  1500 1501 1504 1552  -HSync +Vsync	# 2048x1500 @ 60.00 Hz (GTF) hsync: 93.12 kHz; pclk: 260.74 MHz
```

The "2048x1500_60.00" is just the name of the mode, to be referenced in he Screen section. 260.74 is the dot/pixel clock rate. 2048, 2200, 2424, and 2800 are hdisp, hsyncstart, hsyncend, and htotal values, respectively. 1500, 1501, 1504, and 1552 are vdisp, vsyncstart, vsyncend, and vtotal values, respectively.

I'll try contacting the radeonhd team.

**Important:** I actually put that 2048x1500 resolution into my Xorg.conf file, added to what is above in xorg.conf. The new Xorg.0.log file doesn't even show 2048x1500 as a resolution rejected; so the xserver doesn't seem to be reading my xorg.conf modelines.

---

### Post by dh003i on 2009-03-25
Another idea: Maybe under the "Device" section, I should type in

```
Option "NoRandr"
```

To disable Randr and use standard modesetting from Xorg.conf??

Outside of automatic mode-setting, is there any reason I want randr? (I will be using a dual-screen with this 2048x1536 Sony GDM-F520 CRT and a 3840×2400 VP2290B LCD; the LCD will likely be just as finicky, as it needs a bunch of stuff set on the monitor to even display at all with standard graphics cards.

---

### Post by Yellow Pasque on 2009-03-25
I don't mean to rain on your parade even more, but if you want EXA/Xv acceleration, you need to build the r6xx-r7xx-support git branch of drm if you haven't already:
[http://wiki.x.org/wiki/radeonhd%3Ar6xx_r7xx_branch](http://wiki.x.org/wiki/radeonhd%3Ar6xx_r7xx_branch)

---

### Post by dh003i on 2009-03-25
> **Temüjin said:**
> I don't mean to rain on your parade even more, but if you want EXA/Xv acceleration, you need to build the r6xx-r7xx-support git branch of drm if you haven't already:
[http://wiki.x.org/wiki/radeonhd%3Ar6xx_r7xx_branch](http://wiki.x.org/wiki/radeonhd%3Ar6xx_r7xx_branch)

Yes, I did that; I have

RADEONHD: version 1.2.4, built from git branch master, commit d9c8f9ce

Any insights on the rest of the mess?

---

