---
title: "Why does Ubuntu 8.10 IGNORE xorg.conf modesettings?"
date: 2009-04-20
forum: x86 64-bit Users
---

### Post by dh003i on 2009-04-20
I have a detailed xorg.conf file, with all of the mode-settings to use for my CRT (using fglrx / Catalyst driver), setting the CRT resolution at up to 2048x1536. I had this working with the radeonhd-HEAD drivers, but then I did something and they stopped working (they were buggy anyways, with scroll issues). So I installed the latest Catalyst driver, and it works fine, but only does resolution 1600x1200. I think that it is completely ignoring my xorg.conf settings, as I have 2048x1536 mode-settings specified. 

I think this is a randr issue. When I had the radeonhd driver, the only way I could get max-resolution was by specifying an option to ignore randr. (What the heck, why has this incomplete replacement been fostered on us before it is ready?). How do I do that with Catalyst drivers?

(I'll post xorg.conf and Xorg.0.log later tonight, I'm at work now).

**/etc/X11/xorg.conf:**
```
Section	"ServerLayout"
	Identifier	"DefaultLayout"
	Screen		"Default Screen" 0 0
EndSection

Section	"Files"
EndSection

Section	"Module"
	Load "dri"	#Only works for X1k cards and RS690 IGP at this time
EndSection

Section	"ServerFlags"

	Option	"AIGLX" "On"				# Forced AIGLX rendering to "on"
	Option	"DefaultServerLayout" "DefaultLayout"	# specifies the default ServerLayout section to use in the absence of the -layout command line option.
	Option	"Xinerama" "off"			# Turns Xinerama off
EndSection

Section	"Modes"
	Identifier	"Modes GDM-F520"
	# 9:5 ASPECT RATIO SETTINGS (slightly longer than 16:9)
	# Modline	"XxY_Refresh" Dotclc hdsp hsys hsye htot vdsp vsys vsye vtot
	ModeLine	"720x400_70.00" 26.1 720 736 808 896 400 401 404 417 -hsync +vsync	# 720x400 @ 70.00 Hz (GTF) hsync: 29.19 kHz; pclk: 26.15 MHz
	ModeLine	"720x400_85.00" 32.6 720 744 816 912 400 401 404 421 -hsync +vsync	# 720x400 @ 85.00 Hz (GTF) hsync: 35.78 kHz; pclk: 32.64 MHz
	# 5:4 ASPECT RATIO SETTINGS
	# Modline	"XxY_Refresh" Dotclc hdsp hsys hsye htot vdsp vsys vsye vtot
	ModeLine	"1280x1024_60.00" 108.9 1280 1360 1496 1712 1024 1025 1028 1060 -hsync +vsync	# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
	ModeLine	"1280x1024_75.00" 138.5 1280 1368 1504 1728 1024 1025 1028 1069 -hsync +vsync	# 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
	ModeLine	"1280x1024_85.00" 159.4 1280 1376 1512 1744 1024 1025 1028 1075 -hsync +vsync	# 1280x1024 @ 85.00 Hz (GTF) hsync: 91.38 kHz; pclk: 159.36 MHz
	# 4:3 ASPECT RATIO SETTINGS
	# Modline	"XxY_Refresh" Dotclc hdsp hsys hsye htot vdsp vsys vsye vtot
	ModeLine	"640x480_60.00" 23.9 640 656 720 800 480 481 484 497 -hsync +vsync	# 640x480 @ 60.00 Hz (GTF) hsync: 29.82 kHz; pclk: 23.86 MHz
	ModeLine	"640x480_75.00" 30.7 640 664 728 816 480 481 484 502 -hsync +vsync	# 640x480 @ 75.00 Hz (GTF) hsync: 37.65 kHz; pclk: 30.72 MHz
	ModeLine	"640x480_85.00" 35.7 640 672 736 832 480 481 484 505 -hsync +vsync	# 640x480 @ 85.00 Hz (GTF) hsync: 42.92 kHz; pclk: 35.71 MHz
	ModeLine	"800x600_60.00" 38.2 800 832 912 1024 600 601 604 622 -hsync +vsync	# 800x600 @ 60.00 Hz (GTF) hsync: 37.32 kHz; pclk: 38.22 MHz
	ModeLine	"800x600_75.00" 48.9 800 840 920 1040 600 601 604 627 -hsync +vsync	# 800x600 @ 75.00 Hz (GTF) hsync: 47.03 kHz; pclk: 48.91 MHz
	ModeLine	"800x600_85.00" 56.5 800 840 928 1056 600 601 604 630 -hsync +vsync	# 800x600 @ 85.00 Hz (GTF) hsync: 53.55 kHz; pclk: 56.55 MHz
	ModeLine	"832x624_75.00" 53.2 832 872 960 1088 624 625 628 652 -hsync +vsync	# 832x624 @ 75.00 Hz (GTF) hsync: 48.90 kHz; pclk: 53.20 MHz
	ModeLine	"1024x768_60.00" 64.1 1024 1080 1184 1344 768 769 772 795 -hsync +vsync	# 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
	ModeLine	"1024x768_70.00" 76.2 1024 1080 1192 1360 768 769 772 800 -hsync +vsync	# 1024x768 @ 70.00 Hz (GTF) hsync: 56.00 kHz; pclk: 76.16 MHz
	ModeLine	"1024x768_75.00" 81.8 1024 1080 1192 1360 768 769 772 802 -hsync +vsync	# 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
	ModeLine	"1024x768_85.00" 94.4 1024 1088 1200 1376 768 769 772 807 -hsync +vsync	# 1024x768 @ 85.00 Hz (GTF) hsync: 68.60 kHz; pclk: 94.39 MHz
	ModeLine	"1152x864_60.00" 81.6 1152 1216 1336 1520 864 865 868 895 -hsync +vsync	# 1152x864 @ 60.00 Hz (GTF) hsync: 53.70 kHz; pclk: 81.62 MHz
	ModeLine	"1152x864_75.00" 105.0 1152 1224 1352 1552 864 865 868 902 -hsync +vsync	# 1152x864 @ 75.00 Hz (GTF) hsync: 67.65 kHz; pclk: 104.99 MHz
	ModeLine	"1152x864_85.00" 119.7 1152 1224 1352 1552 864 865 868 907 -hsync +vsync	# 1152x864 @ 85.00 Hz (GTF) hsync: 77.10 kHz; pclk: 119.65 MHz
	ModeLine	"1600x1200_60.00" 161.0 1600 1704 1880 2160 1200 1201 1204 1242 -hsync +vsync	# 1600x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 160.96 MHz
	ModeLine	"1600x1200_65.00" 176.2 1600 1712 1888 2176 1200 1201 1204 1246 -hsync +vsync	# 1600x1200 @ 65.00 Hz (GTF) hsync: 80.99 kHz; pclk: 176.23 MHz
	ModeLine	"1600x1200_70.00" 190.2 1600 1712 1888 2176 1200 1201 1204 1249 -hsync +vsync	# 1600x1200 @ 70.00 Hz (GTF) hsync: 87.43 kHz; pclk: 190.25 MHz
	ModeLine	"1600x1200_75.00" 206.0 1600 1720 1896 2192 1200 1201 1204 1253 -hsync +vsync	# 1600x1200 @ 75.00 Hz (GTF) hsync: 93.97 kHz; pclk: 205.99 MHz
	ModeLine	"1600x1200_85.00" 234.8 1600 1720 1896 2192 1200 1201 1204 1260 -hsync +vsync	# 1600x1200 @ 85.00 Hz (GTF) hsync: 107.10 kHz; pclk: 234.76 MHz
	ModeLine	"1920x1440_75.00" 297.6 1920 2072 2280 2640 1440 1441 1444 1503 -hsync +vsync	# 1920x1440 @ 75.00 Hz (GTF) hsync: 112.73 kHz; pclk: 297.59 MHz
	ModeLine	"1920x1440_85.00" 341.4 1920 2072 2288 2656 1440 1441 1444 1512 -hsync +vsync	# 1920x1440 @ 85.00 Hz (GTF) hsync: 128.52 kHz; pclk: 341.35 MHz
	ModeLine	"2048x1536_60.00" 266.9 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync	# 2048x1536 @ 60.00 Hz (GTF) hsync: 95.34 kHz; pclk: 266.95 MHz
	ModeLine	"2048x1536_73.00" 329.1 2048 2208 2432 2816 1536 1537 1540 1601 -hsync +vsync	# 2048x1536 @ 73.00 Hz (GTF) hsync: 116.87 kHz; pclk: 329.11 MHz
	ModeLine	"2048x1536_75.00" 340.5 2048 2216 2440 2832 1536 1537 1540 1603 -hsync +vsync	# 2048x1536 @ 75.00 Hz (GTF) hsync: 120.22 kHz; pclk: 340.48 MHz
	ModeLine	"2048x1536_85.00" 388.0 2048 2216 2440 2832 1536 1537 1540 1612 -hsync +vsync	# 2048x1536 @ 85.00 Hz (GTF) hsync: 137.02 kHz; pclk: 388.04 MHz
EndSection

Section	"Monitor"
	Identifier	"Sony GDM-F520"
	UseModes	"Modes GDM-F520"
	DisplaySize	406 303		# specified in x y millimeters
	HorizSync	30.0-137.0 	# units in kHz by default
	VertRefresh	48.0-170.0 	# units in Hz by default
	Option		"VendorName" "Sony"
	Option		"ModelName" "GDM-F520"
	Option		"DPMS" "true"
	Option		"TargetRefresh" "85"	# target vertical refresh rate when selecting video modes
	Option		"MinClock" "23"		# minimum dot clock (kHz) supported by monitor
	Option		"MaxClock" "390"		# maximum dot clock (kHz) supported by monitor
	Option		"PreferredMode" "2048x1536_85.00"	# specifies a mode to be marked as the preferred initial mode of the monitor
	Option		"CRT1" "Sony GDM-F520"	# monitor sections may be tied to specific outputs of the video card

EndSection

Section	"Device"
	Option		"ModeDebug" "True"	# Enable printing of additional debugging information about modesetting to the server log.
	Identifier	"ATI Radeon HD4670"
	Driver		"fglrx"
	Option		"DRI" "on"		# turn off if cause problems; experimental in HEAD radeonhd
#	BusID		"PCI:0000:01:00.0"
#	BusID		"PCI:0000:01:00.1"
EndSection

Section	"Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon HD4670"
	Monitor		"Sony GDM-F520"
	DefaultDepth	24
	SubSection	"Display"
		Viewport	0 0
		Virtual		2048 1536	# specifies the virtual screen resolution to be used; 5888 2400 for GDM-F520 + VP2290B
		Depth		24
		Modes		"2048x1536_85.00" "2048x1536_75.00" "2048x1536_73.00" "2048x1536_60.00" "1920x1440_85.00" "1920x1440_75.00" "1600x1200_85.00" "1600x1200_75.00" "1600x1200_65.00" "1600x1200_60.00" "1152x864_85.00" "1152x864_75.00" "1152x864_60.00" "1152x864" "1024x768_85.00" "1024x768_75.00" "1024x768_75.00" "1024x768_70.00" "1024x768_60.00" "832x624_75.00" "800x600_85.00" "800x600_75.00" "800x600_60.00" "640x480_85.00" "640x480_75.00" "640x480_60.00" "1280x1024_85.00" "1280x1024_75.00" "1280x1024_60.00" "720x400_85.00" "720x400_70.00"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Virtual		2048 1536	# specifies the virtual screen resolution to be used; 5888 2400 for GDM-F520 + VP2290B
		Depth		16	
		Modes		"2048x1536_85.00" "2048x1536_75.00" "2048x1536_73.00" "2048x1536_60.00" "1920x1440_85.00" "1920x1440_75.00" "1600x1200_85.00" "1600x1200_75.00" "1600x1200_65.00" "1600x1200_60.00" "1152x864_85.00" "1152x864_75.00" "1152x864_60.00" "1152x864" "1024x768_85.00" "1024x768_75.00" "1024x768_75.00" "1024x768_70.00" "1024x768_60.00" "832x624_75.00" "800x600_85.00" "800x600_75.00" "800x600_60.00" "640x480_85.00" "640x480_75.00" "640x480_60.00" "1280x1024_85.00" "1280x1024_75.00" "1280x1024_60.00" "720x400_85.00" "720x400_70.00"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Virtual		2048 1536	# specifies the virtual screen resolution to be used; 5888 2400 for GDM-F520 + VP2290B
		Depth		8	
		Modes		"2048x1536_85.00" "2048x1536_75.00" "2048x1536_73.00" "2048x1536_60.00" "1920x1440_85.00" "1920x1440_75.00" "1600x1200_85.00" "1600x1200_75.00" "1600x1200_65.00" "1600x1200_60.00" "1152x864_85.00" "1152x864_75.00" "1152x864_60.00" "1152x864" "1024x768_85.00" "1024x768_75.00" "1024x768_75.00" "1024x768_70.00" "1024x768_60.00" "832x624_75.00" "800x600_85.00" "800x600_75.00" "800x600_60.00" "640x480_85.00" "640x480_75.00" "640x480_60.00" "1280x1024_85.00" "1280x1024_75.00" "1280x1024_60.00" "720x400_85.00" "720x400_70.00"
	EndSubSection
EndSection
```

**/var/log/Xorg.0.log**
Note: There is information here about a DVI link plugged in that is for my 9-megapixel VP2290B LCD. I haven't even dare trying to set this up yet, as it is a PITA, and I want to get my CRT working first.
```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux davidjheinrich 2.6.27-11-generic #1 SMP Wed Apr 1 20:53:41 UTC 2009 x86_64
Build Date: 09 March 2009  01:06:41PM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 20 17:49:22 2009
(==) Using config file: "/etc/X11/xorg.conf"
(**) Option "defaultserverlayout" "DefaultLayout"
(**) ServerLayout "DefaultLayout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Sony GDM-F520"
(**) |   |-->Device "ATI Radeon HD4670"
(**) Option "Xinerama" "off"
(**) Option "AIGLX" "On"
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
(++) using VT number 7

(--) PCI:*(0@1:0:0) ATI Technologies Inc RV730XT [Radeon HD 4670] rev 0, Mem @ 0xd0000000/268435456, 0xfe8e0000/65536, I/O @ 0x0000b000/256, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
(II) Loading extension XFree86-DRI
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
	compiled for 7.4.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX disabled
(WW) fglrx: Force AIGLX enabled
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
(II) LoadModule: "fglrx"

(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.59.2
	Module class: X.Org Video Driver
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.59.2
(II) ATI Proprietary Linux Driver Release Identifier: 8.593                                
(II) ATI Proprietary Linux Driver Build Date: Mar 12 2009 23:40:06
(II) Loading PCS database from /etc/ati/amdpcsdb
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
(WW) Video driver ABI version of the X server is 4.1
(II) AMD ASIC control file status: R2 S1 B330 N330 T329
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x9490) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) fglrx(0): pEnt->device->identifier=0x8b5be0
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
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "dri" "on"
(**) fglrx(0): Option "DPMS" "true"
(II) fglrx(0): 10BitPixelFormat disabled by default
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(**) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"

(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.59.2
(--) fglrx(0): Chipset: "ATI Radeon HD 4670" (Chipset = 0x9490)
(--) fglrx(0): (PciSubVendor = 0x1462, PciSubDevice = 0x1590)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfe8e0000
(--) fglrx(0): I/O port at 0x0000b000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 11.9
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV730
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(II) fglrx(0): Using adapter: 1:0.0.
(--) fglrx(0): Video RAM: 524288 kByte, Type: GDDR3
(II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x20000000)
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000101, disabled=0x00000000
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0):  Display1: No EDID information from DDC.
(EE) fglrx(0): Unknown EDID version 0
(II) fglrx(0):  Display1: Failed to get EDID information. 
(II) fglrx(0): Connected Display2: DFP 3 [dfp3]
(II) fglrx(0): Display2 EDID data ---------------------------
(II) fglrx(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) fglrx(0): Year: 2002  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) fglrx(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff005a631134e09d0000
(II) fglrx(0): 	2f0c010380301e782a6492a3574a9c25
(II) fglrx(0): 	1550542fcf00a9408180615945593159
(II) fglrx(0): 	310a01010101d03900d0f36012906880
(II) fglrx(0): 	1310e02c1100001c3130806072601c90
(II) fglrx(0): 	68c81300f02c0100001cad31806072b0
(II) fglrx(0): 	1d4068c81300e02c1100001c000000fd
(II) fglrx(0): 	00095f166911000a2020202020200056
(II) fglrx(0): End of Display2 EDID data --------------------
(II) fglrx(0): Output DFP1 using monitor section Sony GDM-F520
(**) fglrx(0): Option "PreferredMode" "2048x1536_85.00"
(WW) fglrx(0): Option "MinClock" requires a frequency value
(WW) fglrx(0): Option "MaxClock" requires a frequency value
(II) fglrx(0): Output DFP3 has no monitor section
(II) fglrx(0): Output CRT1 has no monitor section
(II) fglrx(0): Output CRT2 has no monitor section
(**) fglrx(0): Option "ModeDebug" "True"
(II) fglrx(0): EDID for output DFP1
(II) fglrx(0): EDID for output DFP3
(II) fglrx(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) fglrx(0): Year: 2002  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) fglrx(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	000000000000000072782830293a2045
(II) fglrx(0): 	4449442028696e20686578293a0a0020
(II) fglrx(0): 	20000a00cf00a9405100000000000000
(II) fglrx(0): 	205593000000000072782830293a2052
(II) fglrx(0): 	616e6765733a2056206d696e3a202569
(II) fglrx(0): 	2056206d61783a20256920487a2c2048
(II) fglrx(0): 	206d696e3a2025692048206d61783a20
(II) fglrx(0): 	2569206b487a2c005100000000000000
(II) fglrx(0): Not using mode "3840x2400" (height too large for virtual size)
(II) fglrx(0): Not using mode "1920x2400" (height too large for virtual size)
(II) fglrx(0): Not using default mode "640x350" (unknown reason)
(II) fglrx(0): Not using default mode "640x400" (unknown reason)
(II) fglrx(0): Not using default mode "720x400" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "800x600" (unknown reason)
(II) fglrx(0): Not using default mode "1280x960" (unknown reason)
(II) fglrx(0): Not using default mode "1280x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "832x624" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Printing probed modes for output DFP3
(II) fglrx(0): Modeline "1920x1200"x41.0  127.17  1920 2024 2224 2528  1200 1201 1204 1229 -hsync +vsync (50.3 kHz)
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 +hsync +vsync (33.7 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 +hsync +vsync (31.1 kHz)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT1
(II) fglrx(0): Not using default mode "640x350" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "720x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x960" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "832x624" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Printing probed modes for output CRT1
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace -hsync +vsync (50.9 kHz)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace -hsync +vsync (46.3 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace -hsync +vsync (43.0 kHz)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace -hsync +vsync (39.2 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 -hsync +vsync (37.0 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT2
(II) fglrx(0): Output DFP1 disconnected
(II) fglrx(0): Output DFP3 connected
(II) fglrx(0): Output CRT1 connected
(II) fglrx(0): Output CRT2 disconnected
(II) fglrx(0): Using exact sizes for initial modes
(II) fglrx(0): Output DFP3 using initial mode 1600x1200
(II) fglrx(0): Output CRT1 using initial mode 1600x1200
(**) fglrx(0): Display dimensions: (406, 303) mm
(**) fglrx(0): DPI set to (128, 128)
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): QBS disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 4.1
(**) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"

(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(II) fglrx(0): [pcie] 2097152 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): Direct rendering enabled
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): Interrupt handler installed at IRQ 2298.
(II) fglrx(0): Finished Initialize PPLIB!
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906
(II) fglrx(0): detected X.org 7.4.2.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit for fglrx driver
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0x7f7b900d5000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.59.2
(II) fglrx(0):     Date: Mar 13 2009
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.27-11-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): Adjust primary surface width to 0x800 for rotation!
(II) fglrx(0): Adjust desktop virtualY to 0x600! for rotation
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01000000
(II) fglrx(0): FBMM initialized for area (0,0)-(2048,2048)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(2048,1536) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 2048 x 512
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Initialized in-driver Xinerama extension
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"

(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 1.0.0
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 94
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Driver provided ScreenToScreenBitBlt replacement
	Driver provided FillSolidRects replacement
(II) fglrx(0): GLESX is enabled
(II) LoadModule: "amdxmm"

(II) Loading /usr/lib/xorg/modules//amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension AMDXVOPL
(II) fglrx(0): UVD2 feature is available 
(II) fglrx(0): Enable composite support successfully
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(WW) fglrx(0): Option "TargetRefresh" is not used
(WW) fglrx(0): Option "MinClock" is not used
(WW) fglrx(0): Option "MaxClock" is not used
(WW) fglrx(0): Option "PreferredMode" is not used
(WW) fglrx(0): Option "CRT1" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using HW cursor of display infrastructure!
(==) fglrx(0): Using software cursor
(II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) fglrx(0): atiddxDisplayScreenLoadPalette: numColors: 256
(--) RandR disabled
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
drmOpenDevice: open result is 13, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 13, (OK)
drmOpenByBusid: drmOpenMinor returns 13
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/lib64/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) fglrx(0): Enable the clock gating!
(II) fglrx(0): Restoring recent mode: 1600x1200@60Hz
(II) fglrx(0): Setting screen physical size to 423 x 317
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
(**) Logitech USB Receiver: Device: "/dev/input/event8"
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
(**) Logitech USB Receiver: Device: "/dev/input/event7"
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found 16 mouse buttons
(II) Logitech USB Receiver: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Composite USB PS2 Converter USB to PS2 Adaptor  V3.10
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: always reports core events
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Device: "/dev/input/event6"
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
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) Wacom driver level: 47-0.8.1-4 $
(**) Wacom Bamboo: always reports core events
(**) Wacom Bamboo device is /dev/input/event9
(**) Wacom Bamboo is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) Wacom Bamboo: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Bamboo" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/event9"
Wacom Bamboo Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 30 for button 1
(==) Wacom USB Bamboo tablet speed=9600 (38400) maxX=14760 maxY=9225 maxZ=511 resX=2540 resY=2540  tilt=disabled
(==) Wacom device "Wacom Bamboo" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(II) fglrx(0): EDID for output DFP1
(II) fglrx(0): EDID for output DFP3
(II) fglrx(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) fglrx(0): Year: 2002  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) fglrx(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	707b1a8e7b7f0000707b1a8e7b7f0000
(II) fglrx(0): 	2f0c010380301e782a6492a3574a9c25
(II) fglrx(0): 	1550542fcf00a9408180615945593159
(II) fglrx(0): 	310a01010101d03900d0f36012906880
(II) fglrx(0): 	1310e02c1100001c3130806072601c90
(II) fglrx(0): 	68c81300f02c0100001cad31806072b0
(II) fglrx(0): 	1d4068c81300e02c1100001c000000fd
(II) fglrx(0): 	00095f166911000a2020202020200056
(II) fglrx(0): Not using mode "3840x2400" (height too large for virtual size)
(II) fglrx(0): Not using mode "1920x2400" (height too large for virtual size)
(II) fglrx(0): Not using default mode "640x350" (unknown reason)
(II) fglrx(0): Not using default mode "640x400" (unknown reason)
(II) fglrx(0): Not using default mode "720x400" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "800x600" (unknown reason)
(II) fglrx(0): Not using default mode "1280x960" (unknown reason)
(II) fglrx(0): Not using default mode "1280x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "832x624" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Printing probed modes for output DFP3
(II) fglrx(0): Modeline "1920x1200"x41.0  127.17  1920 2024 2224 2528  1200 1201 1204 1229 -hsync +vsync (50.3 kHz)
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 +hsync +vsync (33.7 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 +hsync +vsync (31.1 kHz)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT1
(II) fglrx(0): Not using default mode "640x350" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "720x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x960" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "832x624" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Printing probed modes for output CRT1
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace -hsync +vsync (50.9 kHz)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace -hsync +vsync (46.3 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace -hsync +vsync (43.0 kHz)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace -hsync +vsync (39.2 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 -hsync +vsync (37.0 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT2
(II) fglrx(0): EDID for output DFP1
(II) fglrx(0): EDID for output DFP3
(II) fglrx(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) fglrx(0): Year: 2002  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) fglrx(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	707b1a8e7b7f0000707b1a8e7b7f0000
(II) fglrx(0): 	2f0c010380301e782a6492a3574a9c25
(II) fglrx(0): 	1550542fcf00a9408180615945593159
(II) fglrx(0): 	310a01010101d03900d0f36012906880
(II) fglrx(0): 	1310e02c1100001c3130806072601c90
(II) fglrx(0): 	68c81300f02c0100001cad31806072b0
(II) fglrx(0): 	1d4068c81300e02c1100001c000000fd
(II) fglrx(0): 	00095f166911000a2020202020200056
(II) fglrx(0): Not using mode "3840x2400" (height too large for virtual size)
(II) fglrx(0): Not using mode "1920x2400" (height too large for virtual size)
(II) fglrx(0): Not using default mode "640x350" (unknown reason)
(II) fglrx(0): Not using default mode "640x400" (unknown reason)
(II) fglrx(0): Not using default mode "720x400" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "800x600" (unknown reason)
(II) fglrx(0): Not using default mode "1280x960" (unknown reason)
(II) fglrx(0): Not using default mode "1280x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "832x624" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Printing probed modes for output DFP3
(II) fglrx(0): Modeline "1920x1200"x41.0  127.17  1920 2024 2224 2528  1200 1201 1204 1229 -hsync +vsync (50.3 kHz)
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 +hsync +vsync (33.7 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 +hsync +vsync (31.1 kHz)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT1
(II) fglrx(0): Not using default mode "640x350" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "720x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x960" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "832x624" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Printing probed modes for output CRT1
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace -hsync +vsync (50.9 kHz)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace -hsync +vsync (46.3 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace -hsync +vsync (43.0 kHz)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace -hsync +vsync (39.2 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 -hsync +vsync (37.0 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT2
(II) fglrx(0): EDID for output DFP1
(II) fglrx(0): EDID for output DFP3
(II) fglrx(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) fglrx(0): Year: 2002  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) fglrx(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	607b1a8e7b7f0000607b1a8e7b7f0000
(II) fglrx(0): 	2f0c010380301e782a6492a3574a9c25
(II) fglrx(0): 	1550542fcf00a9408180615945593159
(II) fglrx(0): 	310a01010101d03900d0f36012906880
(II) fglrx(0): 	1310e02c1100001c3130806072601c90
(II) fglrx(0): 	68c81300f02c0100001cad31806072b0
(II) fglrx(0): 	1d4068c81300e02c1100001c000000fd
(II) fglrx(0): 	00095f166911000a2020202020200056
(II) fglrx(0): Not using mode "3840x2400" (height too large for virtual size)
(II) fglrx(0): Not using mode "1920x2400" (height too large for virtual size)
(II) fglrx(0): Not using default mode "640x350" (unknown reason)
(II) fglrx(0): Not using default mode "640x400" (unknown reason)
(II) fglrx(0): Not using default mode "720x400" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "800x600" (unknown reason)
(II) fglrx(0): Not using default mode "1280x960" (unknown reason)
(II) fglrx(0): Not using default mode "1280x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "832x624" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Printing probed modes for output DFP3
(II) fglrx(0): Modeline "1920x1200"x41.0  127.17  1920 2024 2224 2528  1200 1201 1204 1229 -hsync +vsync (50.3 kHz)
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 +hsync +vsync (33.7 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 +hsync +vsync (31.1 kHz)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT1
(II) fglrx(0): Not using default mode "640x350" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "720x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x960" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "832x624" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Printing probed modes for output CRT1
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace -hsync +vsync (50.9 kHz)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace -hsync +vsync (46.3 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace -hsync +vsync (43.0 kHz)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace -hsync +vsync (39.2 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 -hsync +vsync (37.0 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT2
(II) fglrx(0): EDID for output DFP1
(II) fglrx(0): EDID for output DFP3
(II) fglrx(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) fglrx(0): Year: 2002  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) fglrx(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	607b1a8e7b7f0000607b1a8e7b7f0000
(II) fglrx(0): 	2f0c010380301e782a6492a3574a9c25
(II) fglrx(0): 	1550542fcf00a9408180615945593159
(II) fglrx(0): 	310a01010101d03900d0f36012906880
(II) fglrx(0): 	1310e02c1100001c3130806072601c90
(II) fglrx(0): 	68c81300f02c0100001cad31806072b0
(II) fglrx(0): 	1d4068c81300e02c1100001c000000fd
(II) fglrx(0): 	00095f166911000a2020202020200056
(II) fglrx(0): Not using mode "3840x2400" (height too large for virtual size)
(II) fglrx(0): Not using mode "1920x2400" (height too large for virtual size)
(II) fglrx(0): Not using default mode "640x350" (unknown reason)
(II) fglrx(0): Not using default mode "640x400" (unknown reason)
(II) fglrx(0): Not using default mode "720x400" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "800x600" (unknown reason)
(II) fglrx(0): Not using default mode "1280x960" (unknown reason)
(II) fglrx(0): Not using default mode "1280x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "832x624" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Printing probed modes for output DFP3
(II) fglrx(0): Modeline "1920x1200"x41.0  127.17  1920 2024 2224 2528  1200 1201 1204 1229 -hsync +vsync (50.3 kHz)
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 +hsync +vsync (33.7 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 +hsync +vsync (31.1 kHz)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT1
(II) fglrx(0): Not using default mode "640x350" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "720x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x960" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "832x624" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Printing probed modes for output CRT1
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace -hsync +vsync (50.9 kHz)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace -hsync +vsync (46.3 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace -hsync +vsync (43.0 kHz)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace -hsync +vsync (39.2 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 -hsync +vsync (37.0 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT2
```

---

### Post by Sutek on 2009-04-20
Try ```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
```
more useful infos on [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

---

### Post by dh003i on 2009-04-20
> **Sutek said:**
> Try ```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
```
more useful infos on [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

Thanks. Tried that, but not luck. My xorg.conf settings are still ignored:

**/var/log/Xorg.0.conf**
```


X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux davidjheinrich 2.6.27-11-generic #1 SMP Wed Apr 1 20:53:41 UTC 2009 x86_64
Build Date: 09 March 2009  01:06:41PM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 20 18:08:49 2009
(==) Using config file: "/etc/X11/xorg.conf"
(**) Option "defaultserverlayout" "DefaultLayout"
(**) ServerLayout "DefaultLayout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Sony GDM-F520"
(**) |   |-->Device "ATI Radeon HD4670"
(**) Option "Xinerama" "off"
(**) Option "AIGLX" "On"
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
(++) using VT number 7

(--) PCI:*(0@1:0:0) ATI Technologies Inc RV730XT [Radeon HD 4670] rev 0, Mem @ 0xd0000000/268435456, 0xfe8e0000/65536, I/O @ 0x0000b000/256, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
(II) Loading extension XFree86-DRI
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
	compiled for 7.4.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX disabled
(WW) fglrx: Force AIGLX enabled
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
(II) LoadModule: "fglrx"

(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.59.2
	Module class: X.Org Video Driver
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.59.2
(II) ATI Proprietary Linux Driver Release Identifier: 8.593                                
(II) ATI Proprietary Linux Driver Build Date: Mar 12 2009 23:40:06
(II) Loading PCS database from /etc/ati/amdpcsdb
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
(WW) Video driver ABI version of the X server is 4.1
(II) AMD ASIC control file status: R2 S1 B330 N330 T329
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x9490) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) fglrx(0): pEnt->device->identifier=0x1889850
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
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "dri" "on"
(**) fglrx(0): Option "UseFastTLS" "1"
(**) fglrx(0): Option "DPMS" "true"
(II) fglrx(0): 10BitPixelFormat disabled by default
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(**) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"

(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.59.2
(--) fglrx(0): Chipset: "ATI Radeon HD 4670" (Chipset = 0x9490)
(--) fglrx(0): (PciSubVendor = 0x1462, PciSubDevice = 0x1590)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfe8e0000
(--) fglrx(0): I/O port at 0x0000b000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 11.9
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV730
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(II) fglrx(0): Using adapter: 1:0.0.
(--) fglrx(0): Video RAM: 524288 kByte, Type: GDDR3
(II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x20000000)
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000101, disabled=0x00000000
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0):  Display1: No EDID information from DDC.
(EE) fglrx(0): Unknown EDID version 0
(II) fglrx(0):  Display1: Failed to get EDID information. 
(II) fglrx(0): Connected Display2: DFP 3 [dfp3]
(II) fglrx(0): Display2 EDID data ---------------------------
(II) fglrx(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) fglrx(0): Year: 2002  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) fglrx(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff005a631134e09d0000
(II) fglrx(0): 	2f0c010380301e782a6492a3574a9c25
(II) fglrx(0): 	1550542fcf00a9408180615945593159
(II) fglrx(0): 	310a01010101d03900d0f36012906880
(II) fglrx(0): 	1310e02c1100001c3130806072601c90
(II) fglrx(0): 	68c81300f02c0100001cad31806072b0
(II) fglrx(0): 	1d4068c81300e02c1100001c000000fd
(II) fglrx(0): 	00095f166911000a2020202020200056
(II) fglrx(0): End of Display2 EDID data --------------------
(II) fglrx(0): Output DFP1 using monitor section Sony GDM-F520
(**) fglrx(0): Option "PreferredMode" "2048x1536_85.00"
(WW) fglrx(0): Option "MinClock" requires a frequency value
(WW) fglrx(0): Option "MaxClock" requires a frequency value
(II) fglrx(0): Output DFP3 has no monitor section
(II) fglrx(0): Output CRT1 has no monitor section
(II) fglrx(0): Output CRT2 has no monitor section
(**) fglrx(0): Option "ModeDebug" "True"
(II) fglrx(0): EDID for output DFP1
(II) fglrx(0): EDID for output DFP3
(II) fglrx(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) fglrx(0): Year: 2002  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) fglrx(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	000000000000000072782830293a2045
(II) fglrx(0): 	4449442028696e20686578293a0a0020
(II) fglrx(0): 	20000a00cf00a9405100000000000000
(II) fglrx(0): 	309790010000000072782830293a2052
(II) fglrx(0): 	616e6765733a2056206d696e3a202569
(II) fglrx(0): 	2056206d61783a20256920487a2c2048
(II) fglrx(0): 	206d696e3a2025692048206d61783a20
(II) fglrx(0): 	2569206b487a2c005100000000000000
(II) fglrx(0): Not using mode "3840x2400" (height too large for virtual size)
(II) fglrx(0): Not using mode "1920x2400" (height too large for virtual size)
(II) fglrx(0): Not using default mode "640x350" (unknown reason)
(II) fglrx(0): Not using default mode "640x400" (unknown reason)
(II) fglrx(0): Not using default mode "720x400" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "800x600" (unknown reason)
(II) fglrx(0): Not using default mode "1280x960" (unknown reason)
(II) fglrx(0): Not using default mode "1280x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "832x624" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Printing probed modes for output DFP3
(II) fglrx(0): Modeline "1920x1200"x41.0  127.17  1920 2024 2224 2528  1200 1201 1204 1229 -hsync +vsync (50.3 kHz)
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 +hsync +vsync (33.7 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 +hsync +vsync (31.1 kHz)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT1
(II) fglrx(0): Not using default mode "640x350" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "720x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x960" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "832x624" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Printing probed modes for output CRT1
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace -hsync +vsync (50.9 kHz)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace -hsync +vsync (46.3 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace -hsync +vsync (43.0 kHz)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace -hsync +vsync (39.2 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 -hsync +vsync (37.0 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT2
(II) fglrx(0): Output DFP1 disconnected
(II) fglrx(0): Output DFP3 connected
(II) fglrx(0): Output CRT1 connected
(II) fglrx(0): Output CRT2 disconnected
(II) fglrx(0): Using exact sizes for initial modes
(II) fglrx(0): Output DFP3 using initial mode 1600x1200
(II) fglrx(0): Output CRT1 using initial mode 1600x1200
(**) fglrx(0): Display dimensions: (406, 303) mm
(**) fglrx(0): DPI set to (128, 128)
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): QBS disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 4.1
(**) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"

(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(II) fglrx(0): [pcie] 2097152 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(**) fglrx(0): UseFastTLS=1
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): Direct rendering enabled
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): Interrupt handler installed at IRQ 2298.
(II) fglrx(0): Finished Initialize PPLIB!
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906
(II) fglrx(0): detected X.org 7.4.2.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit for fglrx driver
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0x7fc859343000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.59.2
(II) fglrx(0):     Date: Mar 13 2009
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.27-11-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): Adjust primary surface width to 0x800 for rotation!
(II) fglrx(0): Adjust desktop virtualY to 0x600! for rotation
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01000000
(II) fglrx(0): FBMM initialized for area (0,0)-(2048,2048)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(2048,1536) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 2048 x 512
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Initialized in-driver Xinerama extension
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"

(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 1.0.0
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 94
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Driver provided ScreenToScreenBitBlt replacement
	Driver provided FillSolidRects replacement
(II) fglrx(0): GLESX is enabled
(II) LoadModule: "amdxmm"

(II) Loading /usr/lib/xorg/modules//amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension AMDXVOPL
(II) fglrx(0): UVD2 feature is available 
(II) fglrx(0): Enable composite support successfully
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(WW) fglrx(0): Option "TargetRefresh" is not used
(WW) fglrx(0): Option "MinClock" is not used
(WW) fglrx(0): Option "MaxClock" is not used
(WW) fglrx(0): Option "PreferredMode" is not used
(WW) fglrx(0): Option "CRT1" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using HW cursor of display infrastructure!
(==) fglrx(0): Using software cursor
(II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) fglrx(0): atiddxDisplayScreenLoadPalette: numColors: 256
(--) RandR disabled
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
drmOpenDevice: open result is 13, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 13, (OK)
drmOpenByBusid: drmOpenMinor returns 13
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/lib64/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) fglrx(0): Enable the clock gating!
(II) fglrx(0): Restoring recent mode: 1600x1200@60Hz
(II) fglrx(0): Setting screen physical size to 423 x 317
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
(**) Logitech USB Receiver: Device: "/dev/input/event8"
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
(**) Logitech USB Receiver: Device: "/dev/input/event7"
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found 16 mouse buttons
(II) Logitech USB Receiver: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Composite USB PS2 Converter USB to PS2 Adaptor  V3.10
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: always reports core events
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Device: "/dev/input/event6"
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
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) Wacom driver level: 47-0.8.1-4 $
(**) Wacom Bamboo: always reports core events
(**) Wacom Bamboo device is /dev/input/event9
(**) Wacom Bamboo is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) Wacom Bamboo: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Bamboo" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/event9"
Wacom Bamboo Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 30 for button 1
(==) Wacom USB Bamboo tablet speed=9600 (38400) maxX=14760 maxY=9225 maxZ=511 resX=2540 resY=2540  tilt=disabled
(==) Wacom device "Wacom Bamboo" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(II) fglrx(0): EDID for output DFP1
(II) fglrx(0): EDID for output DFP3
(II) fglrx(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) fglrx(0): Year: 2002  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) fglrx(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	d05b4157c87f0000d05b4157c87f0000
(II) fglrx(0): 	2f0c010380301e782a6492a3574a9c25
(II) fglrx(0): 	1550542fcf00a9408180615945593159
(II) fglrx(0): 	310a01010101d03900d0f36012906880
(II) fglrx(0): 	1310e02c1100001c3130806072601c90
(II) fglrx(0): 	68c81300f02c0100001cad31806072b0
(II) fglrx(0): 	1d4068c81300e02c1100001c000000fd
(II) fglrx(0): 	00095f166911000a2020202020200056
(II) fglrx(0): Not using mode "3840x2400" (height too large for virtual size)
(II) fglrx(0): Not using mode "1920x2400" (height too large for virtual size)
(II) fglrx(0): Not using default mode "640x350" (unknown reason)
(II) fglrx(0): Not using default mode "640x400" (unknown reason)
(II) fglrx(0): Not using default mode "720x400" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "800x600" (unknown reason)
(II) fglrx(0): Not using default mode "1280x960" (unknown reason)
(II) fglrx(0): Not using default mode "1280x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "832x624" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Printing probed modes for output DFP3
(II) fglrx(0): Modeline "1920x1200"x41.0  127.17  1920 2024 2224 2528  1200 1201 1204 1229 -hsync +vsync (50.3 kHz)
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 +hsync +vsync (33.7 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 +hsync +vsync (31.1 kHz)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT1
(II) fglrx(0): Not using default mode "640x350" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "720x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x960" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "832x624" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Printing probed modes for output CRT1
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace -hsync +vsync (50.9 kHz)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace -hsync +vsync (46.3 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace -hsync +vsync (43.0 kHz)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace -hsync +vsync (39.2 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 -hsync +vsync (37.0 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT2
(II) fglrx(0): EDID for output DFP1
(II) fglrx(0): EDID for output DFP3
(II) fglrx(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) fglrx(0): Year: 2002  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) fglrx(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	a0120b0200000000805b4157c87f0000
(II) fglrx(0): 	2f0c010380301e782a6492a3574a9c25
(II) fglrx(0): 	1550542fcf00a9408180615945593159
(II) fglrx(0): 	310a01010101d03900d0f36012906880
(II) fglrx(0): 	1310e02c1100001c3130806072601c90
(II) fglrx(0): 	68c81300f02c0100001cad31806072b0
(II) fglrx(0): 	1d4068c81300e02c1100001c000000fd
(II) fglrx(0): 	00095f166911000a2020202020200056
(II) fglrx(0): Not using mode "3840x2400" (height too large for virtual size)
(II) fglrx(0): Not using mode "1920x2400" (height too large for virtual size)
(II) fglrx(0): Not using default mode "640x350" (unknown reason)
(II) fglrx(0): Not using default mode "640x400" (unknown reason)
(II) fglrx(0): Not using default mode "720x400" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "800x600" (unknown reason)
(II) fglrx(0): Not using default mode "1280x960" (unknown reason)
(II) fglrx(0): Not using default mode "1280x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "832x624" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Printing probed modes for output DFP3
(II) fglrx(0): Modeline "1920x1200"x41.0  127.17  1920 2024 2224 2528  1200 1201 1204 1229 -hsync +vsync (50.3 kHz)
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 +hsync +vsync (33.7 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 +hsync +vsync (31.1 kHz)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT1
(II) fglrx(0): Not using default mode "640x350" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "720x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x960" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "832x624" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Printing probed modes for output CRT1
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace -hsync +vsync (50.9 kHz)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace -hsync +vsync (46.3 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace -hsync +vsync (43.0 kHz)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace -hsync +vsync (39.2 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 -hsync +vsync (37.0 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT2
(II) fglrx(0): EDID for output DFP1
(II) fglrx(0): EDID for output DFP3
(II) fglrx(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) fglrx(0): Year: 2002  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) fglrx(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	605b4157c87f0000605b4157c87f0000
(II) fglrx(0): 	2f0c010380301e782a6492a3574a9c25
(II) fglrx(0): 	1550542fcf00a9408180615945593159
(II) fglrx(0): 	310a01010101d03900d0f36012906880
(II) fglrx(0): 	1310e02c1100001c3130806072601c90
(II) fglrx(0): 	68c81300f02c0100001cad31806072b0
(II) fglrx(0): 	1d4068c81300e02c1100001c000000fd
(II) fglrx(0): 	00095f166911000a2020202020200056
(II) fglrx(0): Not using mode "3840x2400" (height too large for virtual size)
(II) fglrx(0): Not using mode "1920x2400" (height too large for virtual size)
(II) fglrx(0): Not using default mode "640x350" (unknown reason)
(II) fglrx(0): Not using default mode "640x400" (unknown reason)
(II) fglrx(0): Not using default mode "720x400" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "800x600" (unknown reason)
(II) fglrx(0): Not using default mode "1280x960" (unknown reason)
(II) fglrx(0): Not using default mode "1280x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "832x624" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Printing probed modes for output DFP3
(II) fglrx(0): Modeline "1920x1200"x41.0  127.17  1920 2024 2224 2528  1200 1201 1204 1229 -hsync +vsync (50.3 kHz)
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 +hsync +vsync (33.7 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 +hsync +vsync (31.1 kHz)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT1
(II) fglrx(0): Not using default mode "640x350" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "720x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x960" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "832x624" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Printing probed modes for output CRT1
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace -hsync +vsync (50.9 kHz)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace -hsync +vsync (46.3 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace -hsync +vsync (43.0 kHz)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace -hsync +vsync (39.2 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 -hsync +vsync (37.0 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT2
(II) fglrx(0): EDID for output DFP1
(II) fglrx(0): EDID for output DFP3
(II) fglrx(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) fglrx(0): Year: 2002  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) fglrx(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	f05b4157c87f0000f05b4157c87f0000
(II) fglrx(0): 	2f0c010380301e782a6492a3574a9c25
(II) fglrx(0): 	1550542fcf00a9408180615945593159
(II) fglrx(0): 	310a01010101d03900d0f36012906880
(II) fglrx(0): 	1310e02c1100001c3130806072601c90
(II) fglrx(0): 	68c81300f02c0100001cad31806072b0
(II) fglrx(0): 	1d4068c81300e02c1100001c000000fd
(II) fglrx(0): 	00095f166911000a2020202020200056
(II) fglrx(0): Not using mode "3840x2400" (height too large for virtual size)
(II) fglrx(0): Not using mode "1920x2400" (height too large for virtual size)
(II) fglrx(0): Not using default mode "640x350" (unknown reason)
(II) fglrx(0): Not using default mode "640x400" (unknown reason)
(II) fglrx(0): Not using default mode "720x400" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "800x600" (unknown reason)
(II) fglrx(0): Not using default mode "1280x960" (unknown reason)
(II) fglrx(0): Not using default mode "1280x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "832x624" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Printing probed modes for output DFP3
(II) fglrx(0): Modeline "1920x1200"x41.0  127.17  1920 2024 2224 2528  1200 1201 1204 1229 -hsync +vsync (50.3 kHz)
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 +hsync +vsync (33.7 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 +hsync +vsync (31.1 kHz)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT1
(II) fglrx(0): Not using default mode "640x350" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "720x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x960" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "832x624" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Printing probed modes for output CRT1
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace -hsync +vsync (50.9 kHz)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace -hsync +vsync (46.3 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace -hsync +vsync (43.0 kHz)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace -hsync +vsync (39.2 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 -hsync +vsync (37.0 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT2
(II) fglrx(0): EDID for output DFP1
(II) fglrx(0): EDID for output DFP3
(II) fglrx(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) fglrx(0): Year: 2002  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) fglrx(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	805c4157c87f0000805c4157c87f0000
(II) fglrx(0): 	2f0c010380301e782a6492a3574a9c25
(II) fglrx(0): 	1550542fcf00a9408180615945593159
(II) fglrx(0): 	310a01010101d03900d0f36012906880
(II) fglrx(0): 	1310e02c1100001c3130806072601c90
(II) fglrx(0): 	68c81300f02c0100001cad31806072b0
(II) fglrx(0): 	1d4068c81300e02c1100001c000000fd
(II) fglrx(0): 	00095f166911000a2020202020200056
(II) fglrx(0): Not using mode "3840x2400" (height too large for virtual size)
(II) fglrx(0): Not using mode "1920x2400" (height too large for virtual size)
(II) fglrx(0): Not using default mode "640x350" (unknown reason)
(II) fglrx(0): Not using default mode "640x400" (unknown reason)
(II) fglrx(0): Not using default mode "720x400" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "800x600" (unknown reason)
(II) fglrx(0): Not using default mode "1280x960" (unknown reason)
(II) fglrx(0): Not using default mode "1280x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "832x624" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Printing probed modes for output DFP3
(II) fglrx(0): Modeline "1920x1200"x41.0  127.17  1920 2024 2224 2528  1200 1201 1204 1229 -hsync +vsync (50.3 kHz)
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 +hsync +vsync (33.7 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 +hsync +vsync (31.1 kHz)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT1
(II) fglrx(0): Not using default mode "640x350" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "720x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x960" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "832x624" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Printing probed modes for output CRT1
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace -hsync +vsync (50.9 kHz)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace -hsync +vsync (46.3 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace -hsync +vsync (43.0 kHz)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace -hsync +vsync (39.2 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 -hsync +vsync (37.0 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT2
(II) fglrx(0): EDID for output DFP1
(II) fglrx(0): EDID for output DFP3
(II) fglrx(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) fglrx(0): Year: 2002  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) fglrx(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	805b4157c87f0000805b4157c87f0000
(II) fglrx(0): 	2f0c010380301e782a6492a3574a9c25
(II) fglrx(0): 	1550542fcf00a9408180615945593159
(II) fglrx(0): 	310a01010101d03900d0f36012906880
(II) fglrx(0): 	1310e02c1100001c3130806072601c90
(II) fglrx(0): 	68c81300f02c0100001cad31806072b0
(II) fglrx(0): 	1d4068c81300e02c1100001c000000fd
(II) fglrx(0): 	00095f166911000a2020202020200056
(II) fglrx(0): Not using mode "3840x2400" (height too large for virtual size)
(II) fglrx(0): Not using mode "1920x2400" (height too large for virtual size)
(II) fglrx(0): Not using default mode "640x350" (unknown reason)
(II) fglrx(0): Not using default mode "640x400" (unknown reason)
(II) fglrx(0): Not using default mode "720x400" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "800x600" (unknown reason)
(II) fglrx(0): Not using default mode "1280x960" (unknown reason)
(II) fglrx(0): Not using default mode "1280x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "832x624" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Printing probed modes for output DFP3
(II) fglrx(0): Modeline "1920x1200"x41.0  127.17  1920 2024 2224 2528  1200 1201 1204 1229 -hsync +vsync (50.3 kHz)
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 +hsync +vsync (33.7 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 +hsync +vsync (31.1 kHz)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT1
(II) fglrx(0): Not using default mode "640x350" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "720x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x960" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "832x624" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Printing probed modes for output CRT1
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace -hsync +vsync (50.9 kHz)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace -hsync +vsync (46.3 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace -hsync +vsync (43.0 kHz)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace -hsync +vsync (39.2 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 -hsync +vsync (37.0 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT2
(II) fglrx(0): EDID for output DFP1
(II) fglrx(0): EDID for output DFP3
(II) fglrx(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) fglrx(0): Year: 2002  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) fglrx(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	605b4157c87f0000605b4157c87f0000
(II) fglrx(0): 	2f0c010380301e782a6492a3574a9c25
(II) fglrx(0): 	1550542fcf00a9408180615945593159
(II) fglrx(0): 	310a01010101d03900d0f36012906880
(II) fglrx(0): 	1310e02c1100001c3130806072601c90
(II) fglrx(0): 	68c81300f02c0100001cad31806072b0
(II) fglrx(0): 	1d4068c81300e02c1100001c000000fd
(II) fglrx(0): 	00095f166911000a2020202020200056
(II) fglrx(0): Not using mode "3840x2400" (height too large for virtual size)
(II) fglrx(0): Not using mode "1920x2400" (height too large for virtual size)
(II) fglrx(0): Not using default mode "640x350" (unknown reason)
(II) fglrx(0): Not using default mode "640x400" (unknown reason)
(II) fglrx(0): Not using default mode "720x400" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "800x600" (unknown reason)
(II) fglrx(0): Not using default mode "1280x960" (unknown reason)
(II) fglrx(0): Not using default mode "1280x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "832x624" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Printing probed modes for output DFP3
(II) fglrx(0): Modeline "1920x1200"x41.0  127.17  1920 2024 2224 2528  1200 1201 1204 1229 -hsync +vsync (50.3 kHz)
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 +hsync +vsync (33.7 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 +hsync +vsync (31.1 kHz)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT1
(II) fglrx(0): Not using default mode "640x350" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "720x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x960" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "832x624" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Printing probed modes for output CRT1
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace -hsync +vsync (50.9 kHz)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace -hsync +vsync (46.3 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace -hsync +vsync (43.0 kHz)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace -hsync +vsync (39.2 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 -hsync +vsync (37.0 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT2
(II) fglrx(0): EDID for output DFP1
(II) fglrx(0): EDID for output DFP3
(II) fglrx(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) fglrx(0): Year: 2002  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) fglrx(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	605b4157c87f0000605b4157c87f0000
(II) fglrx(0): 	2f0c010380301e782a6492a3574a9c25
(II) fglrx(0): 	1550542fcf00a9408180615945593159
(II) fglrx(0): 	310a01010101d03900d0f36012906880
(II) fglrx(0): 	1310e02c1100001c3130806072601c90
(II) fglrx(0): 	68c81300f02c0100001cad31806072b0
(II) fglrx(0): 	1d4068c81300e02c1100001c000000fd
(II) fglrx(0): 	00095f166911000a2020202020200056
(II) fglrx(0): Not using mode "3840x2400" (height too large for virtual size)
(II) fglrx(0): Not using mode "1920x2400" (height too large for virtual size)
(II) fglrx(0): Not using default mode "640x350" (unknown reason)
(II) fglrx(0): Not using default mode "640x400" (unknown reason)
(II) fglrx(0): Not using default mode "720x400" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "800x600" (unknown reason)
(II) fglrx(0): Not using default mode "1280x960" (unknown reason)
(II) fglrx(0): Not using default mode "1280x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "832x624" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Printing probed modes for output DFP3
(II) fglrx(0): Modeline "1920x1200"x41.0  127.17  1920 2024 2224 2528  1200 1201 1204 1229 -hsync +vsync (50.3 kHz)
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 +hsync +vsync (33.7 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 +hsync +vsync (31.1 kHz)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT1
(II) fglrx(0): Not using default mode "640x350" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "720x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x960" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "832x624" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Printing probed modes for output CRT1
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace -hsync +vsync (50.9 kHz)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace -hsync +vsync (46.3 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace -hsync +vsync (43.0 kHz)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace -hsync +vsync (39.2 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 -hsync +vsync (37.0 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT2
(II) fglrx(0): EDID for output DFP1
(II) fglrx(0): EDID for output DFP3
(II) fglrx(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) fglrx(0): Year: 2002  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) fglrx(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	805b4157c87f0000805b4157c87f0000
(II) fglrx(0): 	2f0c010380301e782a6492a3574a9c25
(II) fglrx(0): 	1550542fcf00a9408180615945593159
(II) fglrx(0): 	310a01010101d03900d0f36012906880
(II) fglrx(0): 	1310e02c1100001c3130806072601c90
(II) fglrx(0): 	68c81300f02c0100001cad31806072b0
(II) fglrx(0): 	1d4068c81300e02c1100001c000000fd
(II) fglrx(0): 	00095f166911000a2020202020200056
(II) fglrx(0): Not using mode "3840x2400" (height too large for virtual size)
(II) fglrx(0): Not using mode "1920x2400" (height too large for virtual size)
(II) fglrx(0): Not using default mode "640x350" (unknown reason)
(II) fglrx(0): Not using default mode "640x400" (unknown reason)
(II) fglrx(0): Not using default mode "720x400" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "800x600" (unknown reason)
(II) fglrx(0): Not using default mode "1280x960" (unknown reason)
(II) fglrx(0): Not using default mode "1280x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "832x624" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Printing probed modes for output DFP3
(II) fglrx(0): Modeline "1920x1200"x41.0  127.17  1920 2024 2224 2528  1200 1201 1204 1229 -hsync +vsync (50.3 kHz)
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 +hsync +vsync (33.7 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 +hsync +vsync (31.1 kHz)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT1
(II) fglrx(0): Not using default mode "640x350" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "720x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x960" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "832x624" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Printing probed modes for output CRT1
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace -hsync +vsync (50.9 kHz)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace -hsync +vsync (46.3 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace -hsync +vsync (43.0 kHz)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace -hsync +vsync (39.2 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 -hsync +vsync (37.0 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT2
(II) fglrx(0): EDID for output DFP1
(II) fglrx(0): EDID for output DFP3
(II) fglrx(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) fglrx(0): Year: 2002  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) fglrx(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	a05c4157c87f0000e0ccac0200000000
(II) fglrx(0): 	2f0c010380301e782a6492a3574a9c25
(II) fglrx(0): 	1550542fcf00a9408180615945593159
(II) fglrx(0): 	310a01010101d03900d0f36012906880
(II) fglrx(0): 	1310e02c1100001c3130806072601c90
(II) fglrx(0): 	68c81300f02c0100001cad31806072b0
(II) fglrx(0): 	1d4068c81300e02c1100001c000000fd
(II) fglrx(0): 	00095f166911000a2020202020200056
(II) fglrx(0): Not using mode "3840x2400" (height too large for virtual size)
(II) fglrx(0): Not using mode "1920x2400" (height too large for virtual size)
(II) fglrx(0): Not using default mode "640x350" (unknown reason)
(II) fglrx(0): Not using default mode "640x400" (unknown reason)
(II) fglrx(0): Not using default mode "720x400" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "800x600" (unknown reason)
(II) fglrx(0): Not using default mode "1280x960" (unknown reason)
(II) fglrx(0): Not using default mode "1280x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "832x624" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Printing probed modes for output DFP3
(II) fglrx(0): Modeline "1920x1200"x41.0  127.17  1920 2024 2224 2528  1200 1201 1204 1229 -hsync +vsync (50.3 kHz)
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 +hsync +vsync (33.7 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 +hsync +vsync (31.1 kHz)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT1
(II) fglrx(0): Not using default mode "640x350" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "720x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x960" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1792x1344" (hsync out of range)
(II) fglrx(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1856x1392" (hsync out of range)
(II) fglrx(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "832x624" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Printing probed modes for output CRT1
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace -hsync +vsync (50.9 kHz)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace -hsync +vsync (46.3 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace -hsync +vsync (43.0 kHz)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace -hsync +vsync (39.2 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 -hsync +vsync (37.0 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): EDID for output CRT2
```

---

### Post by Yellow Pasque on 2009-04-21
In the Screen section, try adding:
```
Option "UseEDID" "false"
```

---

### Post by dh003i on 2009-04-22
> **Temüjin said:**
> In the Screen section, try adding:
```
Option "UseEDID" "false"
```

Thanks for the suggestion. 

Trying that results in me getting a weird jittered green/cyan/magenta GDM login screen which doesn't work. (I then don't have any control, can't even CTRL ALT DEL to reboot).

---

### Post by bodhi.zazen on 2009-04-22
xorg.conf is depreciated as of xorg 7 .

The idea was (is) to have better hardware detection out of the box. 

It is still buggy, as you can see, and IMO they should have continued with xorg.conf during the transition.

Alas the old ways are becoming forgotten and old edits to xorg.conf sometimes fail.

---

### Post by dh003i on 2009-04-22
> **bodhi.zazen said:**
> xorg.conf is depreciated as of xorg 7 .

The idea was (is) to have better hardware detection out of the box. 

It is still buggy, as you can see, and IMO they should have continued with xorg.conf during the transition.

Alas the old ways are becoming forgotten and old edits to xorg.conf sometimes fail.

What the freaking hell? How do I get it back? 

Randr sucks! I paid freaking $500 for the best CRT ever made with a 2048x1536 resolution; and now I can only use it at 1600x1200. Really blows.

And I also have a 9-megapixel LCD (the VP2290b). 

This is awful.

---

### Post by bodhi.zazen on 2009-04-22
downgrade Ubuntu ?

What videocard are you using ? ATI ? google search you ati card + ubuntu 9.04 or linux.

ATI uses proprietary drivers, you can ask ATI for linux drivers.

---

### Post by dh003i on 2009-04-22
also, using he "randr" way to set resolutions, it still doesn't work!

```
$ **gtf 2048 1536 60**

  # 2048x1536 @ 60.00 Hz (GTF) hsync: 95.34 kHz; pclk: 266.95 MHz
  Modeline "2048x1536_60.00"  266.95  2048 2200 2424 2800  1536 1537 1540 1589  -HSync +Vsync

$ **xrandr --newmode "2048x1536_60.00"  266.95  2048 2200 2424 2800  1536 1537 1540 1589  -HSync +Vsync**

$ **xrandr --addmode CRT1 "2048x1536_60.00"**
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  161 (RANDR)
  Minor opcode of failed request:  18 ()
  Serial number of failed request:  17
  Current serial number in output stream:  18
```

---

### Post by dh003i on 2009-04-22
> **bodhi.zazen said:**
> downgrade Ubuntu ?

What videocard are you using ? ATI ? google search you ati card + ubuntu 9.04 or linux.

ATI uses proprietary drivers, you can ask ATI for linux drivers.

I'm using Ubuntu 8.10. My GPU is the ATI Radeon HD4670 and the Catalyst drivers.

---

### Post by jrevillug on 2009-04-24
I am having much the same problem at the moment, only with Fedora.

I have a Dell D1626HT monitor connected to the VGA output of my on-board graphic card.  I have nothing attached to the DVI port.

My xorg.conf file includes all the formation needed to get a resolution of 1600x1200 at a refresh rate of 85Hz (the maximum that my monitor can handle).

Despite that, the refresh rate can't be set to above 60Hz.

Having studied the Xorg.0.log file, I noticed that the driver was assigning my Monitor0 section to the DVI port, rather than to my CRT.  At the same time, EDID failed, meaning that the driver has no information about the monitor to set the appropriate refresh rates.

Having looked at your Xorg.0.log, your PC is doing the same thing.  I haven't been able to find a workaround yet - despite trying to add a 'fake monitor' entry to xorg.conf to use the DVI output.

However, I have previously had my monitor, along with this graphics card working properly with Linux, although I think it was with a previous version of the driver.

I'll update you if I find anything to fix it, and would be grateful if you could do the same.

James

P.s. [Here](http://forums.fedoraforum.org/showthread.php?t=220309) is a link to my thread on the fedora Forum - although I haven't had anyother contributions so far.

---

### Post by jrevillug on 2009-04-25
FIXED IT!

I disabled RandR1.2 by doing the following:

     ```

     su
nano /etc/ati/amdpcsdb 
[/code

In the section 
    [code]
      [AMDPCSROOT/SYSTEM/DDX] 

```add
     
      ```
EnableRandR12=Sfalse 
```Save and exit.

Then 
     
     ```
su
nano /etc/X11/xorg.conf 
```and add to the 'Device' Section
     
     ```
Option "EnableRandR12" "false" 
```I then restarted X (Ctrl+Alt+bakspace) and opened both xorg.conf and xorg.0.log as root. I set ignoreEDID to true (since my monitor isn't giving decent results) and took a modeline out of the log file, copied it into xorg.conf and added the name of that mode to the list of modes under the display subsection.

Here is my new xorg.conf:
     
     ```
# Xorg configuration created by livna-config-display

Section "ServerLayout"
    Identifier     "single head configuration"
    Screen      0  "Screen0" 0 0
EndSection

Section "Files"
    ModulePath   "/usr/lib64/xorg/modules/extensions/fglrx"
    ModulePath   "/usr/lib64/xorg/modules"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "AIGLX" "on"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    VendorName   "Dell"
    ModelName    "D1626HT"
    HorizSync    31.0 - 107.0
    VertRefresh  50.0 - 160.0
Modeline "1600x1200x85.0"  229.50  1600 1664 1856 2160  1200 1201 1204 1250
Modeline "1600x1200x75.0"  202.50  1600 1664 1856 2160  1200 1201 1204 1250
  
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Videocard0"
    Driver      "fglrx"
    Option        "OpenGLOverlay" "off"
    Option        "VideoOverlay" "on"
#    Option        "ForceMonitors" "crt1"
    option        "EnbleRandR12" "false"
#    option        "ignoreEDID" "true"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Videocard0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes "1600x1200x85.0" "1600x1200x75.0"
    EndSubSection
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
EndSection 
```I know that modelines are old, but it works - I have 1600x1200 resolution with no flickering.  I'm happy.

In your case, I suspect that you will get away with leaving modelines out of it and using EDID (don't add the Option "IgnoreEDID" line).

James

---

### Post by dh003i on 2009-04-25
Thanks a lot! I'll give that a try after I troubleshoot the upgrade to 9.04 (I don't want to do all this work and then find out it's nullified in 9.04).

---

