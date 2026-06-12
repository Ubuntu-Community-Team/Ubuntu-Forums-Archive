---
title: "Resolution display problems after fresh Jaunty/9.04 install"
date: 2009-05-10
forum: x86 64-bit Users
---

### Post by dh003i on 2009-05-10
Hi all,

I'm having some resolution issues with a fresh install of Kubuntu 9.04, which I hope you guys can help with. 

**_The Problem_**

I can't change the resolution on my CRT, the Sony GDM-F520 which supports resolutions up to 2048 x 1536 @ 85 Hz; I also have a ViewSonic VP2290B LCD plugged in, but it is turned off, as I don't want to deal with that yet (max resolution 3840 x 2400 @ up to 12.7 Hz, due to only 1x single-link DVI connection). The CRT defaults to 1024x768 @ 60 Hz, and that's it. [FONT="Courier New"]KRandRtray[/FONT] shows resolutions only up to 1360x768, but I can't change the resolution from the default resolution (clicking on these other resolutions does nothing). 

Double clicking on [FONT="Courier New"]KRandRtray[/FONT] to bring up the [FONT="Courier New"]Configure Display[/FONT] windows and then clicking on [FONT="Courier New"]_I_dentify Outputs[/FONT] shows both *DVI-I_1/digital* and *DVI-I_2/analog* as being on the same monitor -- my Sony CRT! 

I can rotate the screen from [FONT="Courier New"]KRandRtray[/FONT] using the rotate menu options under either *DVI-I_1/digital* or *DVI-I_2/analog*. 

So it seems like maybe it thinks both outputs go to the same display? And thus is choosing the only resolution that both displays share (1024x768)? But this is wrong; one DVI-D output on my GPU is connected to a DVI-to-VGA adapter, which is plugged into my CRT; the other one is connected to one end of an LFH-60 split cable for my VP2290b. 

**_Background: Upgrade to 9.04 borked, did fresh install_**

I had a lot of problems after upgrading to 9.04 / Jaunty from 8.10, so I just did a fresh install of 9.04. This solved most of the problems, and I now have a functional desktop.

_**RadeonHD Drivers for ATI Radeon HD4670**_

For reference, [I followed this guide (precisely) to install the **radeonhd** drivers]("https://help.ubuntu.com/community/RadeonHD"). My hardware is as follows:

[LIST]
[*]ATI Radeon HD4670 (512 MB)
[*]Sony GDM-F520 CRT (max resolution 2048 x 1536 @ up to 85 Hz)
[*]ViewSonic VP2290B LCD (max resolution 3840 x 2400 @ up to 12.7 Hz, due to only 1x single-link DVI connection)
[/LIST]

Both of the monitors are plugged into the computer, although the VP2290B is turned off.

_**/etc/X11/xorg.conf**_

```
Section "Monitor"
	Identifier	"Sony GDM-F520"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Sony GDM-F520"
	Device		"ATI Radeon HD4670"
EndSection

Section "Device"
	Identifier	"ATI Radeon HD4670"
        Driver		"radeonhd"
        Option		"DRI" "on"
        Option		"AccelMethod" "EXA"
EndSection

Section "DRI"
        Mode		0666
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection
```

**_xrandr output_**
For DVI-I_2/analog, I added the 2048x1536_60.00 entry; but it doesn't show in Krandtray, and I can't select any of the resolutions.
```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 3840 x 3840
DVI-I_1/digital connected 1024x768+0+0 (normal left inverted right x axis y axis) 480mm x 300mm
   3840x2400      12.7 +
   1920x2400      20.1
   1920x1200      40.9
   1600x1200      59.9
   1280x1024      75.0     59.9
   1024x768       84.9     75.1     70.1     60.0*
   800x600        84.7     72.2     75.0     60.3     56.2
   640x480        84.4     75.0     72.8     60.0
DVI-I_1/analog disconnected (normal left inverted right x axis y axis)
DVI-I_2/digital disconnected (normal left inverted right x axis y axis)
DVI-I_2/analog connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8
   1152x864       60.0
   1024x768       60.0*
   800x600        60.3
   640x480        59.9
   2048x1536_60.00   60.0
```

**_Warnings and Errors in /var/log/Xorg.0.log_**
```
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
...
(WW) RADEONHD(0): rhdAtomAllocateFbScratch: FW FB scratch area not located at the end of VRAM. Scratch End: 0x84fec VRAM End: 0x10000000
(II) RADEONHD(0): Cannot get VRAM scratch space. Allocating in main memory instead
...
(WW) RADEONHD(0): Direct rendering for R600 and up forced on - This is NOT officially supported yet and may cause instability or lockups
...
(EE) RADEONHD(0): RHDHdmiInit: unknown HDMI output type
...
(II) RADEONHD(0): RandR: Adding RRoutput DVI-I_1/digital for Output AtomOutputUniphyC
(II) RADEONHD(0): RandR: Adding RRoutput DVI-I_1/analog for Output AtomOutputDACB
(II) RADEONHD(0): RandR: Adding RRoutput DVI-I_2/digital for Output AtomOutputUniphyA
(II) RADEONHD(0): RandR: Adding RRoutput DVI-I_2/analog for Output AtomOutputDACA
(II) RADEONHD(0): Output DVI-I_1/digital using monitor section Sony GDM-F520
(II) RADEONHD(0): Output DVI-I_1/digital has no monitor section
(II) RADEONHD(0): Output DVI-I_1/analog has no monitor section
(II) RADEONHD(0): Output DVI-I_2/digital has no monitor section
(II) RADEONHD(0): Output DVI-I_2/analog has no monitor section
...
(EE) AIGLX error: dlopen of /usr/lib/dri/r600_dri.so failed (/usr/lib/dri/r600_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
```

**_/var/log/Xorg.0.log_**
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux davidjheinrich-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May 10 12:28:57 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Sony GDM-F520"
(**) |   |-->Device "ATI Radeon HD4670"
(**) Option "DontZap" "False"
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
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) ATI Technologies Inc RV730XT [Radeon HD 4670] rev 0, Mem @ 0xd0000000/268435456, 0xfe8e0000/65536, I/O @ 0x0000b000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
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
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "radeonhd"
(II) Loading /usr/lib/xorg/modules/drivers//radeonhd_drv.so
(II) Module radeonhd: vendor="AMD GPG"
	compiled for 1.6.0, module version = 1.2.5
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
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
	R700  : Radeon R700.
	RV710 : Radeon HD4570, HD4350.
	RV730 : Radeon HD4670, HD4650.
	RV740 : Radeon HD4770. EXPERIMENTAL AND UNTESTED.
	RV770 : Radeon HD 4800 Series; Everest, K2, Denali ATI FirePro.
	RV790 : Radeon HD 4890.
	M92   : Mobility Radeon HD4330, HD4530, HD4570. EXPERIMENTAL.
	M93   : Mobility Radeon M93. EXPERIMENTAL AND UNTESTED.
	M96   : Mobility Radeon HD4600.
	M97   : Mobility Radeon HD4860. EXPERIMENTAL AND UNTESTED.
	M98   : Mobility Radeon HD4850, HD4870.

(II) RADEONHD: version 1.2.5, built from git branch master, commit 4be5f715

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
(II) RADEONHD(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) RADEONHD(0): Depth 24, (--) framebuffer bpp 32
(**) RADEONHD(0): Option "AccelMethod" "EXA"
(**) RADEONHD(0): Option "DRI"
(**) RADEONHD(0): Selected EXA 2D acceleration.
(II) RADEONHD(0): Unknown card detected: 0x9490:0x1462:0x1590.
	If - and only if - your card does not work or does not work optimally
	please contact radeonhd@opensuse.org to help rectify this.
	Use the subject: 0x9490:0x1462:0x1590: <name of board>
	and *please* describe the problems you are seeing
	in your message.
(--) RADEONHD(0): Detected an RV730 on an unidentified card
(II) RADEONHD(0): Mapped IO @ 0xfe8e0000 to 0x7f12f3557000 (size 0x00010000)
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
(II) RADEONHD(0): Setting AtomOutputUniphyC to incoherent
(II) RADEONHD(0): I2C device "RHD I2C line 4:E-EDID segment register" registered at address 0x60.
(II) RADEONHD(0): I2C device "RHD I2C line 4:ddc2" registered at address 0xA0.
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): EDID vendor "VSC", prod id 13329
(II) RADEONHD(0): Using EDID range info for horizontal sync
(II) RADEONHD(0): Using EDID range info for vertical refresh
(II) RADEONHD(0): Printing DDC gathered Modelines:
(II) RADEONHD(0): Modeline "3840x2400"x0.0  148.00  3840 3944 4328 4816  2400 2401 2404 2418 -hsync +vsync (30.7 kHz)
(II) RADEONHD(0): Modeline "1920x2400"x0.0  123.37  1920 2024 2224 2528  2400 2401 2404 2428 -hsync +vsync (48.8 kHz)
(II) RADEONHD(0): Modeline "1920x1200"x0.0  127.17  1920 2024 2224 2528  1200 1201 1204 1229 -hsync +vsync (50.3 kHz)
(II) RADEONHD(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEONHD(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEONHD(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEONHD(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEONHD(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEONHD(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEONHD(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEONHD(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEONHD(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEONHD(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEONHD(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEONHD(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEONHD(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEONHD(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEONHD(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEONHD(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEONHD(0): Modeline "640x400"x70.0   23.35  640 656 720 800  400 401 404 417 -hsync +vsync (29.2 kHz)
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: none
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Setting AtomOutputDACA to incoherent
(II) RADEONHD(0): I2C device "RHD I2C line 3:E-EDID segment register" registered at address 0x60.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): Output DVI-I_1/digital connected
(II) RADEONHD(0): Output DVI-I_1/analog disconnected
(II) RADEONHD(0): Output DVI-I_2/digital disconnected
(II) RADEONHD(0): Output DVI-I_2/analog connected
(II) RADEONHD(0): Using fuzzy aspect match for initial modes
(II) RADEONHD(0): Output DVI-I_1/digital using initial mode 1024x768
(II) RADEONHD(0): Output DVI-I_2/analog using initial mode 1024x768
(II) RADEONHD(0): RandR 1.2 support enabled
(==) RADEONHD(0): RGB weight 888
(==) RADEONHD(0): Default visual is TrueColor
(==) RADEONHD(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEONHD(0): Using 3840x3840 Framebuffer with 3840 pitch
(II) RADEONHD(0): FB: Allocated ScanoutBuffer at offset 0x00008000 (size = 0x03840000)
(**) RADEONHD(0): Display dimensions: (480, 300) mm
(**) RADEONHD(0): DPI set to (203, 325)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEONHD(0): FB: Allocated Offscreen Buffer at offset 0x03848000 (size = 0x01998000)
(II) RADEONHD(0): FB: Allocated DRI Back Buffer at offset 0x051E0000 (size = 0x03840000)
(II) RADEONHD(0): FB: Allocated DRI Depth Buffer at offset 0x08A20000 (size = 0x03840000)
(II) RADEONHD(0): FB: Allocated GART table at offset 0x0FFF0000 (size = 0x00010000, end of FB)
(II) RADEONHD(0): FB: Allocated DRI Textures at offset 0x0C260000 (size = 0x03D00000)
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
(II) RADEONHD(0): Mapped IO @ 0xfe8e0000 to 0x7f12f3557000 (size 0x00010000)
(II) RADEONHD(0): Mapped FB @ 0xd0000000 to 0x7f12deeb9000 (size 0x10000000)
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
(II) RADEONHD(0): [pci] 16384 kB allocated with handle 0x10afe200
(II) RADEONHD(0): [pci] ring handle = 0x2effe000
(II) RADEONHD(0): [pci] Ring mapped at 0x7f12decb8000
(II) RADEONHD(0): [pci] Ring contents 0x00000000
(II) RADEONHD(0): [pci] ring read ptr handle = 0x1effe000
(II) RADEONHD(0): [pci] Ring read ptr mapped at 0x7f12f357c000
(II) RADEONHD(0): [pci] Ring read ptr contents 0x00000000
(II) RADEONHD(0): [pci] vertex/indirect buffers handle = 0x2efff000
(II) RADEONHD(0): [pci] Vertex/indirect buffers mapped at 0x7f12deab8000
(II) RADEONHD(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEONHD(0): [pci] GART texture map handle = 0x2f000000
(II) RADEONHD(0): [pci] GART Texture map mapped at 0x7f12ddef8000
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
(II) RADEONHD(0): Mapping DIG1 encoder to KLDSKP_UNIPHYC
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): On Crtc 0 Setting 60.0 Hz Mode: Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEONHD(0): Calling SetCRTC_Timing
(II) RADEONHD(0): SetCRTC_Timing Successful
(II) RADEONHD(0): CallingSetCRTC_OverScan
(II) RADEONHD(0): Set CRTC_OverScan Successful
(II) RADEONHD(0): Calling EnableScaler
(II) RADEONHD(0): EnableScaler Successful
(II) RADEONHD(0): Calling SetPixelClock
(II) RADEONHD(0): SetPixelClock Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling SelectCRTCSource
(II) RADEONHD(0): SelectCRTCSource Successful
(II) RADEONHD(0): Calling SelectCRTCSource
(II) RADEONHD(0): SelectCRTCSource Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling DIG1EncoderControl
(II) RADEONHD(0): DIG1EncoderControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
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
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
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
(II) RADEONHD(0): Setting screen physical size to 270 x 203
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) config/hal: Adding input device Composite USB PS2 Converter USB to PS2 Adaptor  V3.10
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: always reports core events
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Device: "/dev/input/event7"
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found 10 mouse buttons
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found x and y relative axes
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found keys
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Configuring as mouse
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Configuring as keyboard
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: YAxisMapping: buttons 4 and 5
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Composite USB PS2 Converter USB to PS2 Adaptor  V3.10" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_layout: "us"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: (accel) keeping acceleration scheme 1
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: (accel) filter chain progression: 2.00
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: (accel) filter stage 0: 20.00 ms
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: (accel) set acceleration profile 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
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
(**) Logitech USB Receiver: Device: "/dev/input/event9"
(II) Logitech USB Receiver: Found 1 mouse buttons
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"
(II) config/hal: Adding input device Composite USB PS2 Converter USB to PS2 Adaptor  V3.10
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: always reports core events
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Device: "/dev/input/event5"
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found keys
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Configuring as keyboard
(II) XINPUT: Adding extended input device "Composite USB PS2 Converter USB to PS2 Adaptor  V3.10" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_layout: "us"
(II) config/hal: Adding input device Wacom Bamboo
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.2-1 $
(**) Wacom Bamboo: always reports core events
(**) Wacom Bamboo device is /dev/input/event6
(**) Wacom Bamboo (Wacom Bamboo) is not a pad 
(**) Wacom Bamboo is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) Wacom Bamboo: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Bamboo" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/event6"
Wacom Bamboo Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 30 for button 1
(==) Wacom USB Bamboo tablet speed=9600 (38400) maxX=14760 maxY=9225 maxZ=511 resX=2540 resY=2540  tilt=disabled
(==) Wacom device "Wacom Bamboo" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Wacom Bamboo pad
(**) Wacom Bamboo pad: always reports core events
(**) Wacom Bamboo pad device is /dev/input/event6
(**) Wacom Bamboo pad is in relative mode
(**) WACOM: suppress value is 2
(**) Wacom Bamboo pad: reading USB link
(**) Wacom Bamboo pad: threshold = 30
(**) Wacom Bamboo pad: max x = 14760
(**) Wacom Bamboo pad: max y = 9225
(**) Wacom Bamboo pad: max z = 511
(**) Option "BaudRate" "9600"
(**) Wacom Bamboo pad: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Bamboo pad" (type: Wacom Pad)
(==) Wacom device "Wacom Bamboo pad" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Wacom Bamboo cursor
(**) Wacom Bamboo cursor: always reports core events
(**) Wacom Bamboo cursor device is /dev/input/event6
(**) Wacom Bamboo cursor (Wacom Bamboo cursor) is not a pad 
(**) Wacom Bamboo cursor is in relative mode
(**) WACOM: suppress value is 2
(**) Wacom Bamboo cursor: reading USB link
(**) Wacom Bamboo cursor: threshold = 30
(**) Wacom Bamboo cursor: max x = 14760
(**) Wacom Bamboo cursor: max y = 9225
(**) Wacom Bamboo cursor: max z = 511
(**) Option "BaudRate" "9600"
(**) Wacom Bamboo cursor: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Bamboo cursor" (type: Wacom Cursor)
(==) Wacom device "Wacom Bamboo cursor" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Wacom Bamboo eraser
(**) Wacom Bamboo eraser: always reports core events
(**) Wacom Bamboo eraser device is /dev/input/event6
(**) Wacom Bamboo eraser (Wacom Bamboo eraser) is not a pad 
(**) Wacom Bamboo eraser is in absolute mode
(**) WACOM: suppress value is 2
(**) Wacom Bamboo eraser: reading USB link
(**) Wacom Bamboo eraser: threshold = 30
(**) Wacom Bamboo eraser: max x = 14760
(**) Wacom Bamboo eraser: max y = 9225
(**) Wacom Bamboo eraser: max z = 511
(**) Option "BaudRate" "9600"
(**) Wacom Bamboo eraser: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Bamboo eraser" (type: Wacom Eraser)
(==) Wacom device "Wacom Bamboo eraser" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event8"
(II) Logitech USB Receiver: Found 16 mouse buttons
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Configuring as mouse
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0
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
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling DIG1EncoderControl
(II) RADEONHD(0): DIG1EncoderControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling DACAEncoderControl
(II) RADEONHD(0): DACAEncoderControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling DIG1EncoderControl
(II) RADEONHD(0): DIG1EncoderControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling DACAEncoderControl
(II) RADEONHD(0): DACAEncoderControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): On Crtc 0 Setting 60.0 Hz Mode: Modeline "n/a"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEONHD(0): Calling SetCRTC_Timing
(II) RADEONHD(0): SetCRTC_Timing Successful
(II) RADEONHD(0): CallingSetCRTC_OverScan
(II) RADEONHD(0): Set CRTC_OverScan Successful
(II) RADEONHD(0): Calling EnableScaler
(II) RADEONHD(0): EnableScaler Successful
(II) RADEONHD(0): Calling SetPixelClock
(II) RADEONHD(0): SetPixelClock Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling SelectCRTCSource
(II) RADEONHD(0): SelectCRTCSource Successful
(II) RADEONHD(0): Calling SelectCRTCSource
(II) RADEONHD(0): SelectCRTCSource Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling DIG1EncoderControl
(II) RADEONHD(0): DIG1EncoderControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
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
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): On Crtc 0 Setting 60.0 Hz Mode: Modeline "n/a"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEONHD(0): Calling SetCRTC_Timing
(II) RADEONHD(0): SetCRTC_Timing Successful
(II) RADEONHD(0): CallingSetCRTC_OverScan
(II) RADEONHD(0): Set CRTC_OverScan Successful
(II) RADEONHD(0): Calling EnableScaler
(II) RADEONHD(0): EnableScaler Successful
(II) RADEONHD(0): Calling SetPixelClock
(II) RADEONHD(0): SetPixelClock Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling SelectCRTCSource
(II) RADEONHD(0): SelectCRTCSource Successful
(II) RADEONHD(0): Calling SelectCRTCSource
(II) RADEONHD(0): SelectCRTCSource Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling DIG1EncoderControl
(II) RADEONHD(0): DIG1EncoderControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
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
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): On Crtc 0 Setting 60.0 Hz Mode: Modeline "n/a"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEONHD(0): Calling SetCRTC_Timing
(II) RADEONHD(0): SetCRTC_Timing Successful
(II) RADEONHD(0): CallingSetCRTC_OverScan
(II) RADEONHD(0): Set CRTC_OverScan Successful
(II) RADEONHD(0): Calling EnableScaler
(II) RADEONHD(0): EnableScaler Successful
(II) RADEONHD(0): Calling SetPixelClock
(II) RADEONHD(0): SetPixelClock Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling SelectCRTCSource
(II) RADEONHD(0): SelectCRTCSource Successful
(II) RADEONHD(0): Calling SelectCRTCSource
(II) RADEONHD(0): SelectCRTCSource Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling DIG1EncoderControl
(II) RADEONHD(0): DIG1EncoderControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
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
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): On Crtc 0 Setting 60.0 Hz Mode: Modeline "n/a"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEONHD(0): Calling SetCRTC_Timing
(II) RADEONHD(0): SetCRTC_Timing Successful
(II) RADEONHD(0): CallingSetCRTC_OverScan
(II) RADEONHD(0): Set CRTC_OverScan Successful
(II) RADEONHD(0): Calling EnableScaler
(II) RADEONHD(0): EnableScaler Successful
(II) RADEONHD(0): Calling SetPixelClock
(II) RADEONHD(0): SetPixelClock Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling SelectCRTCSource
(II) RADEONHD(0): SelectCRTCSource Successful
(II) RADEONHD(0): Calling SelectCRTCSource
(II) RADEONHD(0): SelectCRTCSource Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling DIG1EncoderControl
(II) RADEONHD(0): DIG1EncoderControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
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
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling DIG1EncoderControl
(II) RADEONHD(0): DIG1EncoderControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling DACAEncoderControl
(II) RADEONHD(0): DACAEncoderControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
```

---

### Post by dh003i on 2009-05-10
This problem was patched by typing:

```
xrandr --output DVI-I_1/digital --off
xrandr --output DVI-I_2/analog --mode 2048x1536_60.00
```

Thanks to the helpful commentary of yangman and bridgman on #radeonhd at freenode:

[INDENT][22:03] <davidjheinrich> can anyone help me with a resolution problem? ( I describe it here: [http://ubuntuforums.org/showthread.php?t=1155462](http://ubuntuforums.org/showthread.php?t=1155462) )
[22:03] <bridgman> looking at it now
[22:04] <davidjheinrich> thanks
[22:04] <-- atokhy has left this channel.
[22:05] <bridgman> there's only one set of edid info for dvi/d and dvi/a, so the driver can only tell which you're using by looking at HPD and load detection
[22:06] <bridgman> if you're using a DVI/I to VGA adapter that asserts HPD (indicating you have a digital connection) then I think the driver will believe you have both
[22:07] <bridgman> note that a plugged-in but turned-off monitor will probably still assert HPD
[22:07] <davidjheinrich> what if I turn it on? (although there's headaches with his, because it's the notorous 9 MP LCD...I thought it'd be easier to just get the CRT up and going 1st)
[22:08] <bridgman> not sure how the driver treats plugged-in-but-not-turned-on displays, especially if pins are shared between the connectors (which occasionally happens)
[22:08] <yangman> your xrandr output says both monitors are actually on. not physically, but they're both enabled and getting signal
[22:09] <bridgman> the Sony is connected via VGA analog ?
[22:09] <davidjheinrich> yes
[22:09] <davidjheinrich> well, wait
[22:09] <davidjheinrich> the Sony has a VGA analog input (being a CRT)...but my GPU has no VGA port, so I use a DVI-to-VGA converter
[22:09] <yangman> xrandr --output DVI-I_1/digital --off; xrandr --output DVI-I_2/analog --mode 1360x768
[22:10] <bridgman> I think radeonhd actually detects the monitor using HPD, which is sometimes problematic
[22:10] <-- egbert has left this server (Read error: 110 (Connection timed out)).
[22:10] <bridgman> as I understand it HPD is really to give the card a whack upside the head and tell it to look at EDID
[22:10] <davidjheinrich> ok, sweet, that worked...now I'm at 2048x1536
[22:13] <davidjheinrich> ok, now, oddly enough, despite that xrandr command working, KRandRTray still doesn't show 2048x1536 on my DVI/analog
[22:14] <yangman> probably a krandrtray bug
[22:14] <bridgman> does closing it and reopening help ?
[22:15] <davidjheinrich> nope, still shows only up to 1360x768 (not 2048x1536)...but at least it's in really small text ;-)
[22:15] <bridgman> ;)
[22:15] <bridgman> maybe it's reading EDID each time or something
[22:15] <bridgman> xrandr shows you the right info ?
[22:17] <davidjheinrich> yae, xrandr shows me all the info...BUT I manually added the 2048x1536_60.00 entry using gtf
[22:17] --> weissj has joined this channel (n=weissj@cpe-069-134-226-104.nc.res.rr.com).
[22:18] <yangman> it's probably not picking up custom modes
[22:18] <bridgman> I guess next step is to update the ubuntu thread and then go find some kde people ?
[22:18] <bridgman> or do you want to try to get the other scary monitor running first ?
[22:18] <davidjheinrich> yea, I'll have to update them that that command worked
[22:19] <davidjheinrich> well, maybe I can try turning it on, see what happens
[22:19] <davidjheinrich> weirdest monitor, it doesn't even show LCD menu on power on if it thinks it isn't connected to the "right" GPU (i.e., Matrox Parhelia)
[22:20] <davidjheinrich> ok, right now, it's just going through the text screen
[22:20] <davidjheinrich> (which it will cycle through infinitely)
[22:22] <davidjheinrich> btw, I'd like to hank both of you, I've been in here a lot, and I remember you guys offering help a lot
[22:25] <davidjheinrich> will typing in the following turn on my LCD and put it at max res? 
[22:25] <davidjheinrich>  xrandr --output DVI-I_1/digital --on; xrandr --output DVI-I_2/analog --mode 3840x2400 
[22:27] <yangman> you don't ahve a Virtual set, so it's going fail if you tile them side-by-side, and also fail in clone mode because it's not a valid mode for the other display
[22:30] <yangman> set a large enough Virtual first. 3840x2400 is already marked as preferred, so just this should work:  xrandr --output DVI-I_1/digital --auto --right-of DVI-I_2/analog
[22:30] --> GerbilSoft has joined this channel (n=GerbilSo@n2-54-51.dhcp.drexel.edu).
[22:35] <-- bridgman has left this server.
[22:40] <davidjheinrich> I should probably set virtual to span 2048x1536 + 3840x2400 (so 5888 x 3936), right?
[22:40] <yangman> 5888x2400 is plenty
[22:41] <davidjheinrich> oh yea, duh, I'm only stacking them 1 way
[22:42] <davidjheinrich> I remember when I was struggling with this before, xorg would ignore my xorg.conf resolution settings...I wonder if that'll still be the case
[22:42] <davidjheinrich> (I had to turn off randr to get it to recognize my resolution settings from xorg.conf)...would the proper way be to make a script to call xrandr and set resolutions upon login?
[22:42] <yangman> it's done differently for RandR
[22:42] <yangman> [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)[/INDENT]

---

### Post by dh003i on 2009-05-11
Ok, so the xrandr commands noted above work for getting the max resolution; but KRandRTray doesn't see that resolution anyways.

And setting up my xorg.conf alone doesn't work; seems to be ignored. I have the following xorg.conf, but with that, it still defaults to low resolution (and doesn't show high res option until I do xrandr commands) upon logging in. What's wrong?

_**/etc/X11/xorg.conf**_
```
Section "Device"
	Identifier	"ATI Radeon HD4670"
	Driver		"radeonhd"
	Option		"DRI" "on"
	Option		"AccelMethod" "EXA"
	Option		"DVI-I_1/digital" "Viewsonic VP2290B"
	Option		"DVI-I_2/analog" "Sony GDM-F520"
EndSection

Section "Modes"
	Identifier	"4:3 CRT"
	Modeline	"2048x1536_73"	329.11  2048 2208 2432 2816  1536 1537 1540 1601  -HSync +Vsync
EndSection

Section "Monitor"
	Identifier	"Sony GDM-F520"
	UseModes	"4:3 CRT"
	Option		"PreferredMode" "2048x1536_73"
EndSection

Section "Monitor"
	Identifier	"Viewsonic VP2290B"
	Option		"Enable" "false"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Sony GDM-F520"
	Device		"ATI Radeon HD4670"
	DefaultDepth	24
	SubSection "Display"
	  Depth		24
	  Virtual	5888 2400
	EndSubSection
EndSection

Section "DRI"
	Mode		0666
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection
```

In my */var/log/Xorg.0.log*, why does it say:
```
**(II) RADEONHD(0): Output DVI-I_1/digital using monitor section Sony GDM-F520**
(**) RADEONHD(0): Option "PreferredMode" "2048x1536_73"
(II) RADEONHD(0): Output DVI-I_1/digital has no monitor section
(II) RADEONHD(0): Output DVI-I_1/analog has no monitor section
(II) RADEONHD(0): Output DVI-I_2/digital has no monitor section
**(II) RADEONHD(0): Output DVI-I_2/analog has no monitor section**
```

**_/var/log/Xorg.0.log**_
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux davidjheinrich-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May 11 01:15:22 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Sony GDM-F520"
(**) |   |-->Device "ATI Radeon HD4670"
(**) Option "DontZap" "False"
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
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) ATI Technologies Inc RV730XT [Radeon HD 4670] rev 0, Mem @ 0xd0000000/268435456, 0xfe8e0000/65536, I/O @ 0x0000b000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
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
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "radeonhd"
(II) Loading /usr/lib/xorg/modules/drivers//radeonhd_drv.so
(II) Module radeonhd: vendor="AMD GPG"
	compiled for 1.6.0, module version = 1.2.5
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
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
	R700  : Radeon R700.
	RV710 : Radeon HD4570, HD4350.
	RV730 : Radeon HD4670, HD4650.
	RV740 : Radeon HD4770. EXPERIMENTAL AND UNTESTED.
	RV770 : Radeon HD 4800 Series; Everest, K2, Denali ATI FirePro.
	RV790 : Radeon HD 4890.
	M92   : Mobility Radeon HD4330, HD4530, HD4570. EXPERIMENTAL.
	M93   : Mobility Radeon M93. EXPERIMENTAL AND UNTESTED.
	M96   : Mobility Radeon HD4600.
	M97   : Mobility Radeon HD4860. EXPERIMENTAL AND UNTESTED.
	M98   : Mobility Radeon HD4850, HD4870.

(II) RADEONHD: version 1.2.5, built from git branch master, commit 4be5f715

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
(**) RADEONHD(0): Option "AccelMethod" "EXA"
(**) RADEONHD(0): Option "DRI" "on"
(**) RADEONHD(0): Selected EXA 2D acceleration.
(II) RADEONHD(0): Unknown card detected: 0x9490:0x1462:0x1590.
	If - and only if - your card does not work or does not work optimally
	please contact radeonhd@opensuse.org to help rectify this.
	Use the subject: 0x9490:0x1462:0x1590: <name of board>
	and *please* describe the problems you are seeing
	in your message.
(--) RADEONHD(0): Detected an RV730 on an unidentified card
(II) RADEONHD(0): Mapped IO @ 0xfe8e0000 to 0x7f11ad221000 (size 0x00010000)
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
(**) RADEONHD(0): Option "PreferredMode" "2048x1536_73"
(II) RADEONHD(0): Output DVI-I_1/digital has no monitor section
(II) RADEONHD(0): Output DVI-I_1/analog has no monitor section
(II) RADEONHD(0): Output DVI-I_2/digital has no monitor section
(II) RADEONHD(0): Output DVI-I_2/analog has no monitor section
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Setting AtomOutputUniphyC to incoherent
(II) RADEONHD(0): I2C device "RHD I2C line 4:E-EDID segment register" registered at address 0x60.
(II) RADEONHD(0): I2C device "RHD I2C line 4:ddc2" registered at address 0xA0.
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): EDID vendor "VSC", prod id 13329
(II) RADEONHD(0): Using EDID range info for horizontal sync
(II) RADEONHD(0): Using EDID range info for vertical refresh
(II) RADEONHD(0): Printing DDC gathered Modelines:
(II) RADEONHD(0): Modeline "3840x2400"x0.0  148.00  3840 3944 4328 4816  2400 2401 2404 2418 -hsync +vsync (30.7 kHz)
(II) RADEONHD(0): Modeline "1920x2400"x0.0  123.37  1920 2024 2224 2528  2400 2401 2404 2428 -hsync +vsync (48.8 kHz)
(II) RADEONHD(0): Modeline "1920x1200"x0.0  127.17  1920 2024 2224 2528  1200 1201 1204 1229 -hsync +vsync (50.3 kHz)
(II) RADEONHD(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEONHD(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEONHD(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEONHD(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEONHD(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEONHD(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEONHD(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEONHD(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEONHD(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEONHD(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEONHD(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEONHD(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEONHD(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEONHD(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEONHD(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEONHD(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEONHD(0): Modeline "640x400"x70.0   23.35  640 656 720 800  400 401 404 417 -hsync +vsync (29.2 kHz)
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: none
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Setting AtomOutputDACA to incoherent
(II) RADEONHD(0): I2C device "RHD I2C line 3:E-EDID segment register" registered at address 0x60.
(II) RADEONHD(0): I2C device "RHD I2C line 3:ddc2" registered at address 0xA0.
(II) RADEONHD(0): Output DVI-I_1/digital connected
(II) RADEONHD(0): Output DVI-I_1/analog disconnected
(II) RADEONHD(0): Output DVI-I_2/digital disconnected
(II) RADEONHD(0): Output DVI-I_2/analog connected
(II) RADEONHD(0): Using fuzzy aspect match for initial modes
(II) RADEONHD(0): Output DVI-I_1/digital using initial mode 1024x768
(II) RADEONHD(0): Output DVI-I_2/analog using initial mode 1024x768
(II) RADEONHD(0): RandR 1.2 support enabled
(==) RADEONHD(0): RGB weight 888
(==) RADEONHD(0): Default visual is TrueColor
(==) RADEONHD(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEONHD(0): Using 5888x2400 Framebuffer with 5888 pitch
(II) RADEONHD(0): FB: Allocated ScanoutBuffer at offset 0x00008000 (size = 0x035E8000)
(**) RADEONHD(0): Display dimensions: (480, 300) mm
(**) RADEONHD(0): DPI set to (311, 203)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEONHD(0): FB: Allocated Offscreen Buffer at offset 0x035F0000 (size = 0x01996000)
(II) RADEONHD(0): FB: Allocated DRI Back Buffer at offset 0x04F86000 (size = 0x035E8000)
(II) RADEONHD(0): FB: Allocated DRI Depth Buffer at offset 0x0856E000 (size = 0x035E8000)
(II) RADEONHD(0): FB: Allocated GART table at offset 0x0FFF0000 (size = 0x00010000, end of FB)
(II) RADEONHD(0): FB: Allocated DRI Textures at offset 0x0BB56000 (size = 0x04400000)
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
(II) RADEONHD(0): Mapped IO @ 0xfe8e0000 to 0x7f11ad221000 (size 0x00010000)
(II) RADEONHD(0): Mapped FB @ 0xd0000000 to 0x7f1198b6b000 (size 0x10000000)
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
(II) RADEONHD(0): [pci] 16384 kB allocated with handle 0x10afe200
(II) RADEONHD(0): [pci] ring handle = 0x2effe000
(II) RADEONHD(0): [pci] Ring mapped at 0x7f119896a000
(II) RADEONHD(0): [pci] Ring contents 0x00000000
(II) RADEONHD(0): [pci] ring read ptr handle = 0x1effe000
(II) RADEONHD(0): [pci] Ring read ptr mapped at 0x7f11ad21e000
(II) RADEONHD(0): [pci] Ring read ptr contents 0x00000000
(II) RADEONHD(0): [pci] vertex/indirect buffers handle = 0x2f000000
(II) RADEONHD(0): [pci] Vertex/indirect buffers mapped at 0x7f119876a000
(II) RADEONHD(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEONHD(0): [pci] GART texture map handle = 0x2f001000
(II) RADEONHD(0): [pci] GART Texture map mapped at 0x7f1197baa000
(II) RADEONHD(0): [drm] register handle = 0xfe8e0000
(II) RADEONHD(0): [dri] Visual configs initialized
(II) RADEONHD(0): [DRI] installation complete
(II) RADEONHD(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEONHD(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEONHD(0): [drm] dma control initialized, using IRQ 16
(II) RADEONHD(0): [drm] Initialized kernel GART heap manager, 12320768
(II) RADEONHD(0): Direct rendering enabled
(II) RADEONHD(0): Using DRM Command Processor (indirect) for acceleration.
(II) EXA(0): Offscreen pixmap area of 26828800 bytes
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
(II) RADEONHD(0): Mapping DIG1 encoder to KLDSKP_UNIPHYC
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): On Crtc 0 Setting 60.0 Hz Mode: Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEONHD(0): Calling SetCRTC_Timing
(II) RADEONHD(0): SetCRTC_Timing Successful
(II) RADEONHD(0): CallingSetCRTC_OverScan
(II) RADEONHD(0): Set CRTC_OverScan Successful
(II) RADEONHD(0): Calling EnableScaler
(II) RADEONHD(0): EnableScaler Successful
(II) RADEONHD(0): Calling SetPixelClock
(II) RADEONHD(0): SetPixelClock Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling SelectCRTCSource
(II) RADEONHD(0): SelectCRTCSource Successful
(II) RADEONHD(0): Calling SelectCRTCSource
(II) RADEONHD(0): SelectCRTCSource Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling DIG1EncoderControl
(II) RADEONHD(0): DIG1EncoderControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
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
(WW) RADEONHD(0): Option "PreferredMode" is not used
(--) RandR disabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
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
(II) RADEONHD(0): Setting screen physical size to 270 x 203
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) RADEONHD(0): Calling BlankCRTC
(II) RADEONHD(0): BlankCRTC Successful
(II) config/hal: Adding input device Composite USB PS2 Converter USB to PS2 Adaptor  V3.10
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: always reports core events
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Device: "/dev/input/event7"
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found 10 mouse buttons
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found x and y relative axes
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found keys
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Configuring as mouse
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Configuring as keyboard
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: YAxisMapping: buttons 4 and 5
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Composite USB PS2 Converter USB to PS2 Adaptor  V3.10" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_layout: "us"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: (accel) keeping acceleration scheme 1
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: (accel) filter chain progression: 2.00
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: (accel) filter stage 0: 20.00 ms
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: (accel) set acceleration profile 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
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
(**) Logitech USB Receiver: Device: "/dev/input/event9"
(II) Logitech USB Receiver: Found 1 mouse buttons
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"
(II) config/hal: Adding input device Composite USB PS2 Converter USB to PS2 Adaptor  V3.10
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: always reports core events
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Device: "/dev/input/event5"
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found keys
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Configuring as keyboard
(II) XINPUT: Adding extended input device "Composite USB PS2 Converter USB to PS2 Adaptor  V3.10" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_layout: "us"
(II) config/hal: Adding input device Wacom Bamboo
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.2-1 $
(**) Wacom Bamboo: always reports core events
(**) Wacom Bamboo device is /dev/input/event6
(**) Wacom Bamboo (Wacom Bamboo) is not a pad 
(**) Wacom Bamboo is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) Wacom Bamboo: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Bamboo" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/event6"
Wacom Bamboo Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 30 for button 1
(==) Wacom USB Bamboo tablet speed=9600 (38400) maxX=14760 maxY=9225 maxZ=511 resX=2540 resY=2540  tilt=disabled
(==) Wacom device "Wacom Bamboo" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Wacom Bamboo pad
(**) Wacom Bamboo pad: always reports core events
(**) Wacom Bamboo pad device is /dev/input/event6
(**) Wacom Bamboo pad is in relative mode
(**) WACOM: suppress value is 2
(**) Wacom Bamboo pad: reading USB link
(**) Wacom Bamboo pad: threshold = 30
(**) Wacom Bamboo pad: max x = 14760
(**) Wacom Bamboo pad: max y = 9225
(**) Wacom Bamboo pad: max z = 511
(**) Option "BaudRate" "9600"
(**) Wacom Bamboo pad: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Bamboo pad" (type: Wacom Pad)
(==) Wacom device "Wacom Bamboo pad" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Wacom Bamboo cursor
(**) Wacom Bamboo cursor: always reports core events
(**) Wacom Bamboo cursor device is /dev/input/event6
(**) Wacom Bamboo cursor (Wacom Bamboo cursor) is not a pad 
(**) Wacom Bamboo cursor is in relative mode
(**) WACOM: suppress value is 2
(**) Wacom Bamboo cursor: reading USB link
(**) Wacom Bamboo cursor: threshold = 30
(**) Wacom Bamboo cursor: max x = 14760
(**) Wacom Bamboo cursor: max y = 9225
(**) Wacom Bamboo cursor: max z = 511
(**) Option "BaudRate" "9600"
(**) Wacom Bamboo cursor: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Bamboo cursor" (type: Wacom Cursor)
(==) Wacom device "Wacom Bamboo cursor" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Wacom Bamboo eraser
(**) Wacom Bamboo eraser: always reports core events
(**) Wacom Bamboo eraser device is /dev/input/event6
(**) Wacom Bamboo eraser (Wacom Bamboo eraser) is not a pad 
(**) Wacom Bamboo eraser is in absolute mode
(**) WACOM: suppress value is 2
(**) Wacom Bamboo eraser: reading USB link
(**) Wacom Bamboo eraser: threshold = 30
(**) Wacom Bamboo eraser: max x = 14760
(**) Wacom Bamboo eraser: max y = 9225
(**) Wacom Bamboo eraser: max z = 511
(**) Option "BaudRate" "9600"
(**) Wacom Bamboo eraser: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Bamboo eraser" (type: Wacom Eraser)
(==) Wacom device "Wacom Bamboo eraser" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event8"
(II) Logitech USB Receiver: Found 16 mouse buttons
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Configuring as mouse
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: stoped with 1 channels, 48000 Hz sampling rate, 8 bits per sample,
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: 0x00 IEC60958 status bits and 0x00 category code
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): On Crtc 1 Setting 60.0 Hz Mode: Modeline "n/a"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEONHD(0): Calling SetCRTC_Timing
(II) RADEONHD(0): SetCRTC_Timing Successful
(II) RADEONHD(0): CallingSetCRTC_OverScan
(II) RADEONHD(0): Set CRTC_OverScan Successful
(II) RADEONHD(0): Calling EnableScaler
(II) RADEONHD(0): EnableScaler Successful
(II) RADEONHD(0): Calling SetPixelClock
(II) RADEONHD(0): SetPixelClock Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling SelectCRTCSource
(II) RADEONHD(0): SelectCRTCSource Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling DIG1EncoderControl
(II) RADEONHD(0): DIG1EncoderControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling DAC2OutputControl
(II) RADEONHD(0): DAC2OutputControl Successful
(II) RADEONHD(0): Calling DACBEncoderControl
(II) RADEONHD(0): DACBEncoderControl Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling UNIPHYTransmitterControl
(II) RADEONHD(0): UNIPHYTransmitterControl Successful
(II) RADEONHD(0): Calling DIG1EncoderControl
(II) RADEONHD(0): DIG1EncoderControl Successful
(II) RADEONHD(0): Calling DAC2OutputControl
(II) RADEONHD(0): DAC2OutputControl Successful
(II) RADEONHD(0): Calling DACBEncoderControl
(II) RADEONHD(0): DACBEncoderControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): On Crtc 0 Setting 59.8 Hz Mode: Modeline "n/a"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
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
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): On Crtc 0 Setting 60.0 Hz Mode: Modeline "n/a"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
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
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC1OutputControl
(II) RADEONHD(0): DAC1OutputControl Successful
(II) RADEONHD(0): Calling EnableCRTC
(II) RADEONHD(0): EnableCRTC Successful
(II) RADEONHD(0): Calling EnableCRTCMemReq
(II) RADEONHD(0): EnableCRTCMemReq Successful
(II) RADEONHD(0): On Crtc 0 Setting 73.0 Hz Mode: Modeline "n/a"  329.11  2048 2208 2432 2816  1536 1537 1540 1601 -hsync +vsync
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
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): EDID data for VSC-3411
(II) RADEONHD(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) RADEONHD(0): Year: 2002  Week: 47
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) RADEONHD(0): Gamma: 2.20
(II) RADEONHD(0): DPMS capabilities: Off
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) RADEONHD(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) RADEONHD(0): Supported VESA Video Modes:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): 640x480@72Hz
(II) RADEONHD(0): 640x480@75Hz
(II) RADEONHD(0): 800x600@56Hz
(II) RADEONHD(0): 800x600@60Hz
(II) RADEONHD(0): 800x600@72Hz
(II) RADEONHD(0): 800x600@75Hz
(II) RADEONHD(0): 1024x768@60Hz
(II) RADEONHD(0): 1024x768@70Hz
(II) RADEONHD(0): 1024x768@75Hz
(II) RADEONHD(0): 1280x1024@75Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported Future Video Modes:
(II) RADEONHD(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEONHD(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEONHD(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEONHD(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEONHD(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEONHD(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) RADEONHD(0): Supported additional Video Mode:
(II) RADEONHD(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) RADEONHD(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) RADEONHD(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0): 	00ffffffffffff005a631134e09d0000
(II) RADEONHD(0): 	2f0c010380301e782a6492a3574a9c25
(II) RADEONHD(0): 	1550542fcf00a9408180615945593159
(II) RADEONHD(0): 	310a01010101d03900d0f36012906880
(II) RADEONHD(0): 	1310e02c1100001c3130806072601c90
(II) RADEONHD(0): 	68c81300f02c0100001cad31806072b0
(II) RADEONHD(0): 	1d4068c81300e02c1100001c000000fd
(II) RADEONHD(0): 	00095f166911000a2020202020200056
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
(II) RADEONHD(0): Calling DAC_LoadDetection
(II) RADEONHD(0): DAC_LoadDetection Successful
(II) RADEONHD(0): AtomOutputDACA: Sensed Output: VGA
```

---

### Post by Maddmaxx on 2009-08-25
[http://ubuntuforums.org/showthread.php?t=1248220](http://ubuntuforums.org/showthread.php?t=1248220) Post # 6... It's a start, but WTF?

---

