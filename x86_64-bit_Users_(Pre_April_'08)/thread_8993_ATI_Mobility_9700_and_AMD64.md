---
title: "ATI Mobility 9700 and AMD64"
date: 2004-12-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by pirivan on 2004-12-23
Hello,

I installed Warty in my new laptop and I can't get X to work. Ubuntu detects the right video card and the X config file seems to have the right stuff in it. But the X server fails to load and the X log message that I get doesn't tell me anything about the error(s).

At this point my only suspicious is the fact that I am running the amd64 port. Could it be that the ati driver in Ubuntu doesn't work well with the amd64 arch? Does anyone have a similar video card running with amd64?

Thanks.

---

### Post by Kareema on 2004-12-24
Hi pirivan,

I'm running Ubuntu AMD64 (Warty first, now Hoary) on my AMD Athlon 64 notebook with an ATI Mobility 9700 without any problems (Acer Ferrari 3400). If I remember correctly, the installation of Ubuntu Warty AMD64 finished without any problems and a working X server.

The right module for the graphics card in the /etc/X11/xfree86.config (or xorg.config for Hoary) is the "radeon" module.

There's currently no DRI module or ATI closed source driver available for the ATI Mobility 9700 under the AMD64 architecture. So there will be no 3D acceleration available at the moment. But ATI has plans for releasing a closed source driver for the AMD64 architecture in the upcoming release of their linux drivers. It has been scheduled for December...

---

### Post by thamiral on 2005-01-13
Hello Kareema and Pirivan,

I just finished an install of Warty on my Gateway 7405GX (AMD64 3200 + ATI Mobility 9600 - 64MB) and I had the same problem that Pirivan was having. 

I upgraded to Hoary to get the Newer version of X and then I managed to get 2D working with the "ati" driver... The "vesa" driver gives me garbled output for Tuxracer while the "ati" driver goes into software rendering mode for 3D (e.g. Tuxracer)

I am not sure about the satus of the ATI drivers since I still dont see support for 3D from the drivers that ATI is currently working on. (Especially since they still need to work on those 64 bit drivers)

I guess Kareema got really lucky getting Warty to work out of the box for the Acer Ferrari... I would really be interested in knowing what you did :)...

I will try to keep the both of you posted if there are any changes with those ATI drivers if you two promise to do the same.   :D 
 
Sincerely,

Taha

---

### Post by Kareema on 2005-01-13
The only drivers that support direct 3D rendering for Radeon 9700 and above at this time are the proprietary ATI drivers (closed source). There are some open source projects going on, but they are not usable yet. This is because ATI only gave away the specifications for older Radeon cards (up to Radeon 9600).

But good news for all people waiting for 3D support for newer Radeon chips under the AMD64 architecture: Next Monday (17.1.), new drivers will be released which exactly support these specifications and an Ubuntu package is ready for release, too. Search the forum for more information.

---

### Post by dJCL on 2005-01-13
On my first instal with a 9700 on my AMD64 laptop I did not get X either. Turned out to not be the video driver, it was the synaptics touch pad driver, I disabled it and X started fine with the 'ati' driver.

JC

---

### Post by tweek! on 2005-01-14
I had the same problem my first time installing Warty on my AMD64 with 9700... I just did a dpkg-reconfigure xserver-xfree86 (or xorg) and it worked nicely... Since then, every install has resulted in X working fine...

---

### Post by garret on 2005-01-17
I keep hearing that the ATI drivers are supposed to be out today 1/17/05, but am unable to find anything official. Could somebody point me to the source of these rumors?

Thanks

---

### Post by ernstp on 2005-01-17
[QUOTE=garret]I keep hearing that the ATI drivers are supposed to be out today 1/17/05, but am unable to find anything official. Could somebody point me to the source of these rumors?

Thanks[/QUOTE]
 They are out!

(I could post you to the very good source of these not-rumors, but it doesn't seem necessary anymore)

Hmmm, now all we need are some debs!

---

### Post by Kareema on 2005-01-18
OK, debs are out (thanks daniels). This was really fast work, but with some problems. Here is my installation protocol including the problems I had and a work-around to get the drivers installed. Remember: Drivers are only available in Hoary!

[list]
[*]Install linux-restricted-modules 2.6.10-2 (in your preferred flavour). Works without problems.
[*]Installation of xorg-driver-fglrx does not work due to dependency problems with ia32-libs. Here's a work-around (better than just overwriting the files with dpkg --force-overwrite):
[/list] 
```

apt-get install -d xorg-driver-fglrx
dpkg-divert --package xorg-driver-fglrx --add /usr/lib32/libGL.so.1
dpkg-divert --package xorg-driver-fglrx --add /usr/lib32/libGL.so.1.2
dpkg -i /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu1_amd64.deb

``` 

fglrx-driver and fglrx-control are not necessary for the drivers to work correclty. So don't istall them, because there are more dependency problems (which will hopefully solved in future releases of these packages).

UPDATE: xorg-driver-fglrx now works without problems after the last release! Don't do the dpkg-divert stuff. You can install xorg-driver-fglrx and fglrx-control via synaptic. If you did the dpkg-divert stuff and want to update, you have to remove the entries via dpkg-divert --remove.

---

### Post by ernstp on 2005-01-18
[QUOTE=Kareema]OK, debs are out (thanks daniels). This was really fast work, but with some problems. Here is my installation protocol including the problems I had and a work-around to get the drivers installed. Remember: Drivers are only available in Hoary!

[list]
[*]Install linux-restricted-modules 2.6.10-2 (in your preferred flavour). Works without problems.
[*]Installation of xorg-driver-fglrx does not work due to dependency problems with ia32-libs. Here's a work-around (better than just overwriting the files with dpkg --force-overwrite):
[/list] 
```

apt-get install -d xorg-driver-fglrx
dpkg-divert --package xorg-driver-fglrx --add /usr/lib32/libGL.so.1
dpkg-divert --package xorg-driver-fglrx --add /usr/lib32/libGL.so.1.2
dpkg -i /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu1_amd64.deb

``` 

fglrx-driver and fglrx-control are not necessary for the drivers to work correclty. So don't istall them, because there are more dependency problems (which will hopefully solved in future releases of these packages).[/QUOTE]
 I'm getting a hard lockup when using the driver on AMD 64.

fglrxconfig avaliable in any package?

---

### Post by Kareema on 2005-01-18
[QUOTE=ernstp]I'm getting a hard lockup when using the driver on AMD 64.
fglrxconfig avaliable in any package?[/QUOTE]

fglrxconfig is available if you follow my instructions. I had the same problem but solved it by setting 'Option "UseInternalAGPGART" "no"'. And be sure that you don't have composite enabled (if enabled then direct rendering and video overlay don't work)!

fglrxconfig generates a Xfree86Config-4 and not a xorg.conf. But this is better IMHO, because you can let fglrxconfig create the Xfree86Config-4 and transfer the needed parts to xorg.conf. This results in a much cleaner X.org configuration than using fglrxconfig alone (if you know what you are doing).

Here are my xorg.conf as a starting point for others.

Hardware: Laptop Acer Ferrari 3400 with Ubuntu AMD64 and ATI Mobile 9700 at 1400x1050.

xorg.conf:
```

# xorg.conf (X.Org X Window System server configuration file)

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	#InputDevice	"PS/2 Mouse" "SendCoreEvents"
 	InputDevice	"USB Mouse" "SendCoreEvents"
 	#InputDevice	"Serial Mouse" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad" "AlwaysCore" "true"
EndSection

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc:unscaled"
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath     	"/usr/lib/X11/fonts/TrueType/"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
	FontPath 	"/usr/share/fonts/truetype/ttf-xfree86-nonfree"
	FontPath 	"/usr/share/fonts/truetype/freefont"
	FontPath 	"/usr/share/fonts/truetype/openoffice"
	FontPath 	"/usr/share/fonts/truetype/ttf-bitstream-vera"
	FontPath 	"/usr/share/fonts/type1/gsfonts"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	#Load	"xtrap"
	#Load	"GLcore"
	#Load	"bitmap"
	Load	"dbe"				# Double buffer extension
	#Load	"ddc"
	Load	"dri"				# libdri.a
	
	SubSection  "extmod"			# loads the miscellaneous extensions module
		Option    "omit xfree86-dga"	# don't initialise the DGA extension
	EndSubSection
	
	Load	"freetype"
	Load	"glx"				# libglx.a
	#Load	"int10"
	#Load	"record"
	#Load	"speedo"
	Load	"type1"
	#Load	"vbe"
	Load 	"synaptics"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"		"xorg"
	Option		"XkbModel"		"pc105"
	Option		"XkbLayout"		"de"
EndSection

Section "InputDevice"
	Identifier	"Serial Mouse"
	Driver		"mouse"
	Option		"Protocol"		"Microsoft"
	Option		"Device"		"/dev/ttyS0"
	Option		"Emulate3Buttons"	"false"
	Option		"Emulate3Timeout"	"70"
EndSection

Section "InputDevice"
	Identifier "PS/2 Mouse"
	Driver		"mouse"
	Option		"Protocol"		"auto"
	Option		"Device"		"/dev/psaux"
	Option		"Emulate3Buttons"	"false"
	Option		"Emulate3Timeout"	"70"
	Option		"ZAxisMapping"		"4 5"
	Option		"Buttons"		"5"
EndSection

Section "InputDevice"
	Identifier	"USB Mouse"
	Driver		"mouse"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Buttons"		"5"
EndSection

Section "InputDevice"
	Identifier      "Synaptics Touchpad"
	Driver          "synaptics"
	Option		"Corepointer"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"LeftEdge"		"1700"
	Option		"RightEdge"		"5300"
	Option		"TopEdge"		"1700"
	Option		"BottomEdge"		"4200"
	Option		"FingerLow"		"25"
	Option		"FingerHigh"		"30"
	Option		"MaxTapTime"		"180"
	Option		"MaxTapMove"		"220"
	Option		"HorizScrollDelta"	"0"
	Option		"VertScrollDelta"	"0"
	Option		"MinSpeed"		"0.06"
	Option		"MaxSpeed"		"0.12"
	Option		"AccelFactor"		"0.0010"
	Option		"SHMConfig"		"on"
	Option		"Buttons"		"7"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option		"NoAccel"            	# [<bool>]
        #Option		"SWcursor"           	# [<bool>]
        #Option		"Dac6Bit"            	# [<bool>]
        #Option		"Dac8Bit"            	# [<bool>]
        #Option		"PanelOff"           	# [<bool>]
        #Option		"DDCMode"            	# [<bool>]
        #Option		"MonitorLayout"      	# [<str>]
        #Option		"IgnoreEDID"         	# [<bool>]
        #Option		"UseFBDev"           	# [<bool>]
        #Option		"VideoKey"           	# <i>
        #Option		"MergedFB"           	# [<bool>]
        #Option		"CRT2HSync"          	# [<str>]
        #Option		"CRT2VRefresh"       	# [<str>]
        #Option		"CRT2Position"       	# [<str>]
        #Option		"MetaModes"          	# [<str>]
        #Option		"MergedDPI"          	# [<str>]
        #Option		"NoMergedXinerama"   	# [<bool>]
        #Option		"MergedXineramaCRT2IsScreen0" 	# [<bool>]
        #Option		"DisplayPriority"    	# [<str>]
        #Option		"PanelSize"          	# [<str>]
        #Option		"ForceMinDotClock"   	# <freq>
        #Option		"RenderAccel"        	# [<bool>]
        #Option		"SubPixelOrder"      	# [<str>]
        #Option		"ShowCache"          	# [<bool>]
        #Option		"DynamicClocks"      	# [<bool>]
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Driver		"fglrx"
	VendorName	"ATI Technologies Inc"
	BoardName	"RV350 [Mobility Radeon 9700 M11]"
	# ### generic DRI settings ###
	# === disable PnP Monitor  ===
    	#Option                              "NoDDC"
	# === disable/enable XAA/DRI ===
	Option "no_accel"                   "no"
	Option "no_dri"                     "no"
	# === misc DRI settings ===
	Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
	# ### FireGL DDX driver module specific settings ###
	# === Screen Management ===
	Option "DesktopSetup"               "0x00000100" 
	Option "MonitorLayout"              "AUTO, NONE"
	Option "IgnoreEDID"                 "off"
	Option "HSync2"                     "unspecified" 
	Option "VRefresh2"                  "unspecified" 
	Option "ScreenOverlap"              "0" 
	# === TV-out Management ===
	Option "NoTV"                       "no"     
	Option "TVStandard"                 "PAL-B"     
	Option "TVHSizeAdj"                 "0"     
	Option "TVVSizeAdj"                 "0"     
	Option "TVHPosAdj"                  "0"     
	Option "TVVPosAdj"                  "0"     
	Option "TVHStartAdj"                "0"     
	Option "TVColorAdj"                 "0"     
	Option "GammaCorrectionI"           "0x00000000"
	Option "GammaCorrectionII"          "0x00000000"
	# === OpenGL specific profiles/settings ===
	Option "Capabilities"               "0x00000000"
	# === Video Overlay for the Xv extension ===
	Option "VideoOverlay"               "on"
	# === OpenGL Overlay ===
	# Note: When OpenGL Overlay is enabled, Video Overlay
	#       will be disabled automatically
	Option "OpenGLOverlay"              "off"
	# === Center Mode (Laptops only) ===
	Option "CenterMode"                 "off"
	# === Pseudo Color Visuals (8-bit visuals) ===
	Option "PseudoColorVisuals"         "off"
	# === QBS Management ===
	Option "Stereo"                     "off"
	Option "StereoSyncEnable"           "1"
	# === FSAA Management ===
	Option "FSAAEnable"                 "no"
	Option "FSAAScale"                  "1"
	Option "FSAADisableGamma"           "no"
	Option "FSAACustomizeMSPos"         "no"
	Option "FSAAMSPosX0"                "0.000000"
	Option "FSAAMSPosY0"                "0.000000"
	Option "FSAAMSPosX1"                "0.000000"
	Option "FSAAMSPosY1"                "0.000000"
	Option "FSAAMSPosX2"                "0.000000"
	Option "FSAAMSPosY2"                "0.000000"
	Option "FSAAMSPosX3"                "0.000000"
	Option "FSAAMSPosY3"                "0.000000"
	Option "FSAAMSPosX4"                "0.000000"
	Option "FSAAMSPosY4"                "0.000000"
	Option "FSAAMSPosX5"                "0.000000"
	Option "FSAAMSPosY5"                "0.000000"
	# === Misc Options ===
	Option "UseFastTLS"                 "0"
	Option "BlockSignalsOnLock"         "on"
	Option "UseInternalAGPGART"         "no"
	Option "ForceGenericCPU"            "no"
	BusID "PCI:1:0:0"    # vendor=1002, device=4e50
	Screen 0
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	VendorName	"IDT"
	ModelName	"2"
	HorizSync	30.0 - 82.0 # Warning: This may fry old Monitors
  	VertRefresh	50.0 - 70.0 # Very conservative. May flicker.
  	#Option "DPMS" "true"
	Modeline "640x480"     25.175 640  664  760  800   480  491  493  525 #60Hz
  	Modeline "800x600"     40.12  800  848  968 1056   600  601  605  628 #60Hz
  	Modeline "1024x768"    75    1024 1048 1184 1328   768  771  777  806 -hsync -vsync
  	Modeline "1024x768"    85    1024 1056 1152 1360   768  784  787  823
  	ModeLine "1152x864"    65    1152 1168 1384 1480   864  865  875  985 Interlace
  	Modeline "1152x864"    92    1152 1208 1368 1474   864  865  875  895
  	Modeline "1152x864"   110    1152 1240 1324 1552   864  864  876  908
  	Modeline "1152x864"   135    1152 1464 1592 1776   864  864  876  908
  	Modeline "1152x864"   137.65 1152 1184 1312 1536   864  866  885  902 -HSync -VSync
  	Modeline "1280x1024"   80    1280 1296 1512 1568  1024 1025 1037 1165 Interlace
  	Modeline "1280x1024"  110    1280 1328 1512 1712  1024 1025 1028 1054
  	Modeline "1280x1024"  126.5  1280 1312 1472 1696  1024 1032 1040 1068 -HSync -VSync
  	Modeline "1280x1024"  135    1280 1312 1456 1712  1024 1027 1030 1064
  	Modeline "1280x1024"  135    1280 1312 1416 1664  1024 1027 1030 1064
  	Modeline "1280x1024"  157.5  1280 1344 1504 1728  1024 1025 1028 1072 +HSync +VSync
  	Modeline "1280x1024"  181.75 1280 1312 1440 1696  1024 1031 1046 1072 -HSync -VSync
  	Modeline "1400x1050"  129    1400 1464 1656 1960  1050 1051 1054 1100 +HSync +VSync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Monitor		"Standardbildschirm"
	DefaultColorDepth 24
	SubSection "Display"
		Depth 1
		Modes "1400x1050""1280x1024""1152x864""1024x768""800x600"
	EndSubSection
	SubSection "Display"
		Depth 4
		Modes "1400x1050""1280x1024""1152x864""1024x768""800x600"
	EndSubSection
	SubSection "Display"
		Depth 8
		Modes "1400x1050""1280x1024""1152x864""1024x768""800x600"
	EndSubSection
	SubSection "Display"
		Depth 15
		Modes "1400x1050""1280x1024""1152x864""1024x768""800x600"
	EndSubSection
	SubSection "Display"
		Depth 16
		Modes "1400x1050""1280x1024""1152x864""1024x768""800x600"
	EndSubSection
	SubSection "Display"
		Depth 24
		Modes "1400x1050""1280x1024""1152x864""1024x768""800x600"
	EndSubSection
	SubSection "Display"
		Depth 32
		Modes "1400x1050""1280x1024""1152x864""1024x768""800x600"
	EndSubSection
EndSection

Section "ServerFlags"
	# Uncomment this to cause a core dump at the spot where a signal is 
	# received.  This may leave the console in an unusable state, but may
	# provide a better stack trace in the core dump to aid in debugging

	#    Option "NoTrapSignals"

	# Uncomment this to disable the <Crtl><Alt><BS> server abort sequence
	# This allows clients to receive this key event.

	#    Option "DontZap"

	# Uncomment this to disable the <Crtl><Alt><KP_+>/<KP_-> mode switching
	# sequences.  This allows clients to receive these key events.

	#    Option "Dont Zoom"

	# Uncomment this to disable tuning with the xvidtune client. With
	# it the client can still run and fetch card and monitor attributes,
	# but it will not be allowed to change them. If it tries it will
	# receive a protocol error.

	#    Option "DisableVidModeExtension"

	# Uncomment this to enable the use of a non-local xvidtune client. 

	#    Option "AllowNonLocalXvidtune"

	# Uncomment this to disable dynamically modifying the input device
	# (mouse and keyboard) settings. 

	#    Option "DisableModInDev"

	# Uncomment this to enable the use of a non-local client to
	# change the keyboard or mouse settings (currently only xset).

	#    Option "AllowNonLocalModInDev"
	
	Option 		"AllowMouseOpenFail" "true"
EndSection

Section "DRI"
	# Access to OpenGL ICD is allowed for all users:
	Mode 0666
	# Access to OpenGL ICD is restricted to a specific user group:
	#    Group 100    # users
	#    Mode 0660
EndSection

#Section "Extensions"
#	Option		"Composite" "Enabled"
#EndSection

``` 

Direct rendering is working perfect now:

fglrxinfo:
```
 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

```

fgl_glxgears:
```

1199 frames in 5.0 seconds = 239.800 FPS
1773 frames in 5.0 seconds = 354.600 FPS

```

---

### Post by Kareema on 2005-01-18
OK, now I have a problem: Doom 3 and Neverwinter Nights are both 32-bit games that should run on Ubuntu AMD64. UT2004 64-bit runs perfectly with hardware acceleration while NWN 32-bit runs slow and Doom 3 doesn't run at all.

Here's what I get when starting doom3:
```

DOOM 1.1.1286 linux-x86 Nov 24 2004 17:56:04
Hostname: localhost.localdomain
Alias: localhost
Alias: smartbook
local IP: 127.0.0.1
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game00.pk4 with checksum 0x7dafc4d4
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x16cf3b8a
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Current search path:
/home/mark/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/pak000.pk4 (2698 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
/usr/local/games/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5151 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5151 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
Xlib:  extension "XFree86-DGA" missing on display ":0.0".
Failed to detect DGA DirectVideo Mouse
Free86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: Mesa GLX Indirect
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
dlopen(libasound.so.2: cannot open shared object file: No such file or directory) failed: š²W
H²W
@

Alsa is not available
----------- Alsa Shutdown ------------
--------------------------------------
------ OSS Sound Initialization ------
opened sound device '/dev/dsp'
ioctl SNDCTL_SYSINFO failed: Invalid argument
this ioctl is only available in OSS/Linux implementation. If you run OSS/Free, don't bother./dev/dsp - bit rate: 16, channels: 2, frequency: 44100
allocated a mix buffer of 16384 bytes
WARNING: ioctl SNDCTL_DSP_SETTRIGGER PCM_ENABLE_OUTPUT failed: Broken pipe
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
X..GL_ARB_texture_non_power_of_two not found
X..GL_ARB_texture_compression not found
X..GL_EXT_texture_filter_anisotropic not found
...using GL_EXT_texture_lod
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
X..GL_EXT_texture3D not found
X..GL_EXT_stencil_wrap not found
X..GL_NV_register_combiners not found
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
X..GL_ARB_vertex_buffer_object not found
X..GL_ARB_vertex_program not found
X..GL_ARB_fragment_program not found
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
Not available.
----------- R200_Init -----------
Not available.
---------- R_ARB2_Init ----------
Not available.
---------- R_Exp_Init -----------
Disabled at compile time.
---------------------------------
----- R_ReloadARBPrograms -----
glprogs/test.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/test.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/interaction.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/interaction.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/bumpyEnvironment.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/bumpyEnvironment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/ambientLight.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/ambientLight.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/shadow.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/R200_interaction.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_bumpAndLight.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_diffuseColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_specularColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_diffuseAndSpecularColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/environment.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/environment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
-------------------------------
WARNING: vertex array range in virtual memory (SLOW)
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
Shutting down sound hardware
------ OSS Sound Shutdown ------
close sound device
--------------------------------
idRenderSystem::Shutdown()

```

It seems that direct rendering does not work in 32-bit mode with the new ATI drivers 8.8.25 (from Ubuntu Hoary repository). Doom 3 uses indirect rendering as you cann see above. Could the dpkg-diversion (see my post above) be the source of my problems (I doubt it)? I checked the date of /usr/lib32/libGL.so.1.2 and it has been changed today (while installing the ATI drivers). Any ideas?

---

### Post by Kareema on 2005-01-18
I investigated the doom 3/nwn problem a little bit further: Direct rendering works in 64-bit mode but to in 32-bit mode. I copied a glxinfo from a 32-bit system together with the libstdc++.so.6 and ran it. Here is the output:

```

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None

``` 

Does anybody has an idea why this happens? Is it a problem with the new drivers or with the Ubuntu AMD64 system environment? Any ideas what to try next?

---

### Post by ernstp on 2005-01-18
Yes, I had a feeling it was the AGP module, was looking for fglrxconfig so I could make a real config file.
My old one had just driver "fglrx"
Found it, fixed it, everything works.

---

### Post by daniels on 2005-01-19
I don't know why this is happening -- not only do I not own an amd64 (only the motherboard, the rest is slowly on its way here), but I couldn't really debug it anyway, because it's closed-source.

---

### Post by Kareema on 2005-01-19
Hello daniels,

as mentioned in one of my other postings in this thread, internal agpgart is not working for me using a K8T800 chipset (external agpgart works). Today I found a patch for this problem at [http://www.rage3d.com/board/showthread.php?t=33800162](http://www.rage3d.com/board/showthread.php?t=33800162). Would it be possible to incorporate this patch into one of the next releases?

---

### Post by Kareema on 2005-01-19
Here is another pointer for the direct rendering 32-bit problem.

I ran glxinfo 32-bit in verbose mode (LIBGL_DEBUG=verbose):

```

name of display: :0.0
libGL: XF86DRIGetClientDriverName: 8.8.25 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/fglrx_dri.so
libGL error: dlopen /usr/X11R6/lib/modules/dri/fglrx_dri.so failed (/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to find driver: fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.8.25 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/fglrx_dri.so
libGL error: dlopen /usr/X11R6/lib/modules/dri/fglrx_dri.so failed (/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to find driver: fglrx_dri.so
display: :0  screen: 0
direct rendering: No

```

The problem is that it tries to load fglrx_dri.so from /usr/X11R6/lib/modules/dri/ and since this is the 64-bit version, glxinfo  32-bit can't load it. Setting the LD_LIBRARY_PATH to look at /usr/X11R6/lib32/modules/dri/ first didn't solve the problem. Do you know how I can set an environment variable to get the right module loaded? Or what else can I do?

---

### Post by daniels on 2005-01-19
OH, CRAP.  I really hope this problem isn't what I suspect it is.

If it is, it means the proprietary ATI libGL is hard-coding lib instead of lib32 in, because they design for mixed 32 and 64 systems with lib64.  D'oh.

---

### Post by daniels on 2005-01-19
Try the following:
LIBGL_DEBUG=verbose LIBGL_DRIVERS_DIR=/usr/X11R6/lib32/modules/dri glxinfo
if that doesn't work:
LIBGL_DEBUG=verbose LIBGL_DRIVERS_PATH=/usr/X11R6/lib32/modules/dri glxinfo

Hooray for looking at libGL.so.1.2 with vim.

---

### Post by Kareema on 2005-01-19
[QUOTE=daniels]Try the following:
LIBGL_DEBUG=verbose LIBGL_DRIVERS_DIR=/usr/X11R6/lib32/modules/dri glxinfo
if that doesn't work:
LIBGL_DEBUG=verbose LIBGL_DRIVERS_PATH=/usr/X11R6/lib32/modules/dri glxinfo

Hooray for looking at libGL.so.1.2 with vim.[/QUOTE]

Yes, let's praise vim and the person who had the idea to look at libGL.so.1.2  :D 

Thank you very much for your help. Setting 'LIBGL_DRIVERS_DIR=/usr/X11R6/lib32/modules/dri' solved my problems.

---

### Post by daniels on 2005-01-19
Huzzah.  I'm glad they had an environment variable for that.  I wonder if I can patch it in with a vi script at build-time.

---

### Post by daniels on 2005-01-19
Could you please grab [http://people.ubuntu.com/~daniels/libGL.so.1.2](http://people.ubuntu.com/~daniels/libGL.so.1.2), put it in /usr/X11R6/lib32, and try running glxinfo32 or Quake 3 or whatever without LIBGL_DRIVERS_* set?

---

### Post by Kareema on 2005-01-19
[QUOTE=daniels]Could you please grab [http://people.ubuntu.com/~daniels/libGL.so.1.2](http://people.ubuntu.com/~daniels/libGL.so.1.2), put it in /usr/X11R6/lib32, and try running glxinfo32 or Quake 3 or whatever without LIBGL_DRIVERS_* set?[/QUOTE]

Segmentation fault in libGL.so.1.2!

---

### Post by daniels on 2005-01-19
Ho hum.

As a general rule though, if you find some way to set LIBGL_DRIVER_PATH=/usr/X11R6/lib/modules/dri:/usr/X11R6/lib32/modules/dri globally, it will always work.

---

### Post by froust on 2005-01-19
wow... looks like this is going to be an interesting night of installing drivers... *jumps into the deep end*

---

### Post by Mr. Coconut on 2005-01-19
Installing the new drivers turned out to be a breeze. What I did was extract the sources and files from the rpm posted on ATI's website, compile the fglrx module and copy over the other files manually. I did figure out that the items in lib should go in lib32, so that's something to watch for. 

Then I ran fglrxconfig, after having copied over my XFree configuration, copied the driver section from the configuration created by fglrxconfig to the old one, set 'useinternalagpgart = no' and presto.

Actually, it took several resets for me to figure out that the internal agpgart was killing my system, but no mind.

What puzzles me, though, is that ubuntu has not made the driver available for warty. I can think of no reason for this, especially since it has been made available to our xorg using friends using the hoary tree. I don't get it: users of the unfinished product get support for their hardware, but users of the actual current release do not? That makes no sense to me.

In any case, I am happy to now be running a fully operational, 3d capable, pure 64 bit system. Yay!

---

### Post by daniels on 2005-01-19
You were right on the money with 'unfinished product' -- by contrast, Warty is a 'finished product'.  It does not receive updates, except for security.

---

### Post by Mr. Coconut on 2005-01-19
This is not a complaint of any magnitude, nor intended as a whine. It just seems counterintuitive to me to supply significant driver updates only to users of an unstable tree.

---

### Post by daniels on 2005-01-19
It's a decision we made in order to keep Warty a known quantity.  The problem is especially bad with binary drivers -- the new nVidia driver, for instance, has broken significant numbers of older cards.  If we released nVidia 1.0-6629 into Warty, that would've resulted in a massive regression of support, and that's why we don't take risks like this.

---

### Post by blinksilver on 2005-01-20
hey all, sorry if i am missing something obvious, but here is what i did and the error messages i got:

root@M6805:/home/soganess # apt-get install -d xorg-driver-fglrx
Reading Package Lists... Done
Building Dependency Tree... Done
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6542kB of archives.
After unpacking 20.1MB of additional disk space will be used.
Download complete and in download only mode
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
root@M6805:/home/soganess # dpkg-divert --package xorg-driver-fglrx --add /usr/lib32/libGL.so.1
Leaving `diversion of /usr/lib32/libGL.so.1 to /usr/lib32/libGL.so.1.distrib by xorg-driver-fglrx'
root@M6805:/home/soganess # dpkg-divert --package xorg-driver-fglrx --add /usr/lib32/libGL.so.1.2
Leaving `diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/libGL.so.1.2.distrib by xorg-driver-fglrx'
root@M6805:/home/soganess # dpkg -i /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu1_amd64.deb
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu1_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu1_amd64.deb
root@M6805:/home/soganess #

---

### Post by daniels on 2005-01-20
Now ubuntu2 is in the archive, you should just be able to run 'sudo apt-get install xorg-driver-fglrx'.

---

### Post by blinksilver on 2005-01-20
thats for the input but no luck,  ](*,)
tried, just the command, then repeated the whole proccess with that command at the end, no luck,

here is the error message, includeing the original one, thanks for trying:

root@M6805:/home/soganess # apt-get install -d xorg-driver-fglrx
Reading Package Lists... Done
Building Dependency Tree... Done
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6542kB of archives.
After unpacking 20.1MB of additional disk space will be used.
Download complete and in download only mode
root@M6805:/home/soganess # dpkg-divert --package xorg-driver-fglrx --add /usr/lib32/libGL.so.1
Leaving `diversion of /usr/lib32/libGL.so.1 to /usr/lib32/libGL.so.1.distrib by xorg-driver-fglrx'
root@M6805:/home/soganess # dpkg-divert --package xorg-driver-fglrx --add /usr/lib32/libGL.so.1.2
Leaving `diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/libGL.so.1.2.distrib by xorg-driver-fglrx'
root@M6805:/home/soganess # dpkg -i /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu1_amd64.deb
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu1_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu1_amd64.deb
root@M6805:/home/soganess # apt-get install xorg-driver-fglrx
Reading Package Lists... Done
Building Dependency Tree... Done
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6542kB of archives.
After unpacking 20.1MB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 78736 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu2_amd64.deb) ...
dpkg-divert: `diversion of /usr/lib32/libGL.so.1 to /usr/lib32/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx' clashes with `diversion of /usr/lib32/libGL.so.1 to /usr/lib32/libGL.so.1.distrib by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu2_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by daniels on 2005-01-20
Don't do the dpkg-divert stuff -- now it's done, you'll need to undo it:
$ sudo dpkg-divert --package xorg-driver-fglrx --remove /usr/lib32/libGL.so.1
$ sudo dpkg-divert --package xorg-driver-fglrx --remove /usr/lib32/libGL.so.1.2
$ sudo apt-get install --reinstall xorg-driver-fglrx

---

### Post by blinksilver on 2005-01-21
thanks, all is well, everything works, and i now have 3D

---

### Post by Nadir on 2005-01-24
I am having problems getting the fglrx driver working with my amd64+radeon 9700. It's failing to allocate AGP memory.

Here are my specs:

Ubuntu Hoary
Linux dataforte 2.6.10-2-amd64-generic #1 Wed Jan 19 17:14:45 UTC 2005 x86_64 GNU/Linux

I have 
Option "UseInternalAGPGART"         "no"
in my xorg.conf.

This is my log:


drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] loaded kernel module for "fglrx" driver
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xffffff000020a000
(II) fglrx(0): [drm] mapped SAREA 0xffffff000020a000 to 0x2a9558c000
(II) fglrx(0): [drm] framebuffer handle = 0xe0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.8.25
(II) fglrx(0):     Date: Jan 14 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.10-2-amd64-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xfb9f0000
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENOSPC"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xffffff000020a000 at 0x2a9558c000

Can anybody help me ?

Thanks

Tristan

---

### Post by Kareema on 2005-01-25
Hi daniels,


the fglrx module is broken in linux-restricted-modules-2.6.10.2-amd64-k8 (version 2.6.10.3-2):

modprobe -v fglrx:
```

insmod /lib/modules/2.6.10-2-amd64-k8/kernel/drivers/video/fglrx.ko
FATAL: Error inserting fglrx (/lib/modules/2.6.10-2-amd64-k8/kernel/drivers/video/fglrx.ko): No such device

```

dmesg | grep fglrx:
```

[fglrx] Maximum main memory to use for locked dma buffers: 424 MBytes.
[fglrx:firegl_stub_register] *ERROR* Unable to the open some already present DRM kernel module!
[fglrx] Maximum main memory to use for locked dma buffers: 424 MBytes.
[fglrx:firegl_init_32compat_ioctls] *ERROR* unable to register ioctl32 0
[fglrx:firegl_init] *ERROR* Couldn't register compat32 ioctls!

```

lsmod:
```

Module                  Size  Used by
rfcomm                 40432  0
l2cap                  25864  5 rfcomm
bluetooth              52868  4 rfcomm,l2cap
esp6                    9152  0
ah6                     8256  0
ipcomp                  9228  0
esp4                    9472  0
ah4                     7552  0
af_key                 34324  2
xfrm_user              17992  0
wp512                  24064  0
twofish                40320  0
tea                     2944  0
sha512                  5632  0
sha256                  9088  0
sha1                    8576  0
serpent                16768  0
md4                     4224  0
khazad                 20096  0
des                    12224  0
deflate                 4480  0
michael_mic             3008  0
cast6                  18496  0
cast5                  16256  0
crypto_null             2880  0
arc4                    2240  0
blowfish                9024  0
aes                    28032  0
anubis                 10752  0
zlib_deflate           23320  1 deflate
powernow_k8            13448  0
proc_intf               4420  0
freq_table              4872  1 powernow_k8
cpufreq_userspace       5456  1
cpufreq_ondemand        7596  0
cpufreq_powersave       2176  0
serial_cs              11304  1
pcmcia                 25672  3 serial_cs
video                  18760  0
sony_acpi               6864  0
pcc_acpi               13568  0
button                  7776  0
battery                11400  0
container               5120  0
ac                      5640  0
ipv6                  268448  25 esp6,ah6
driverloader          251792  0
af_packet              23308  8
ipt_limit               2944  2
ipt_state               2432  92
ipt_LOG                 7552  2
ipt_REJECT              7552  2
ip_conntrack_ftp       73584  0
ip_conntrack_irc       72816  0
ip_conntrack           52320  3 ipt_state,ip_conntrack_ftp,ip_conntrack_irc
iptable_filter          4352  1
ip_tables              19200  5 ipt_limit,ipt_state,ipt_LOG,ipt_REJECT,iptable_filter
snd_via82xx            29856  2
snd_ac97_codec         80992  1 snd_via82xx
snd_pcm_oss            56676  1
usb_storage            73344  0
snd_mixer_oss          20288  2 snd_pcm_oss
usbhid                 34176  0
snd_pcm               102348  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              26184  1 snd_pcm
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
gameport                4992  1 snd_via82xx
snd_mpu401_uart         8192  1 snd_via82xx
snd_rawmidi            26528  1 snd_mpu401_uart
snd_seq_device          9744  1 snd_rawmidi
snd                    58600  9 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              11360  3 snd
ehci_hcd               33604  0
uhci_hcd               34208  0
tg3                    83908  0
ohci1394               35460  0
ieee1394              385496  1 ohci1394
yenta_socket           22528  1
pcmcia_core            56780  3 serial_cs,pcmcia,yenta_socket
pcspkr                  4024  0
md                     48576  0
dm_mod                 63768  1
capability              5832  0
commoncap               9536  1 capability
eeprom                  8920  0
i2c_sensor              4032  1 eeprom
i2c_viapro              8652  0
i2c_core               24664  3 eeprom,i2c_sensor,i2c_viapro
evdev                  10688  1
joydev                 11264  0
tsdev                   8768  0
parport_pc             40648  1
lp                     13104  0
parport                40844  2 parport_pc,lp
ide_cd                 45192  0
cdrom                  43304  1 ide_cd
rtc                    13320  0
mousedev               13148  1
psmouse                22412  0
sd_mod                 18584  0
scsi_mod              143512  2 usb_storage,sd_mod
ext3                  139664  2
jbd                    60848  1 ext3
mbcache                 9160  1 ext3
ide_generic             1728  0
via82cxxx              14320  1
ide_disk               20800  4
ide_core              150276  5 usb_storage,ide_cd,ide_generic,via82cxxx,ide_disk
unix                   30016  1043
thermal                15692  0
processor              25984  2 powernow_k8,thermal
fan                     5256  0
fbcon                  38688  71
crc32                   4672  1 fbcon
font                    8960  1 fbcon
bitblit                 5888  1 fbcon
vesafb                  7680  1
cfbcopyarea             4288  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             4288  1 vesafb

```

Doesn't seem to be a problem of the linux-restricted-modules package. Downgrading to my previous version (which worked until my last update) did not solve the problem. As I cannot see another DRM kernel module loaded with lsmod it seems that there is a new/modified kernel module in the latest kernel-image that prevents fglrx.ko from loading. Could I be right?

---

### Post by daniels on 2005-01-25
The 'radeon' module for the open-source DRI driver is loaded -- run sudo rmmod radeon first.

---

### Post by Kareema on 2005-01-25
[QUOTE=daniels]The 'radeon' module for the open-source DRI driver is loaded -- run sudo rmmod radeon first.[/QUOTE]

It's not loaded (see my lsmod above).

rmmod radeon:
ERROR: Module radeon does not exist in /proc/modules

Seems to be compiled in?

EDIT: It's not compiled in. less /boot/config-2.6.10-2-amd64-k8 | grep DRM:
```

CONFIG_DRM=y
CONFIG_DRM_TDFX=m
CONFIG_DRM_R128=m
CONFIG_DRM_RADEON=m
CONFIG_DRM_MGA=m
CONFIG_DRM_SIS=m

```

I've got no idea what it could be...

EDIT 2: Downgrading to linux-image-2.6.10-2-amd64-k8_2.6.10-10_amd64 solves the problem. So it is obviously a problem introduced with a kernel update/patch.

---

### Post by Kareema on 2005-01-27
The problem loading the fglrx kernel module introduced in kernel image version 2.6.10-11 is still there in version 2.6.10-12: When trying to load the fglrx module during startup, there's a message saying ''[fglrx:firegl_stub_register] *ERROR* Unable to the open some already present DRM kernel module!".

I cannot find another DRM module loaded (with lsmod) and there's not DRM driver compiled into the kernel (that I could find). My configuration works perfectly when downgrading to kernel image version 2.6.10-10. A diff between the kernel image configurations and looking through the kernel image changelog did not help much either. I only found one hint: Could the newly introduced MGA DRM driver backported from 2.6.11rc1 have something to do with the problem?

---

### Post by singy on 2005-01-27
Hi,

I have a FSC Amilo 1630 Amd64 and hoary running on it.
Like in  threads [http://www.ubuntuforums.org/showthread.php?t=12686](http://www.ubuntuforums.org/showthread.php?t=12686) told, I am using the kernel 2.6.10-10 and everthing runs perfect. Width the kernel 2.6.10-11, I had also problems.
greetings

---

### Post by Nadir on 2005-01-28
[QUOTE=Kareema]The problem loading the fglrx kernel module introduced in kernel image version 2.6.10-11 is still there in version 2.6.10-12: When trying to load the fglrx module during startup, there's a message saying ''[fglrx:firegl_stub_register] *ERROR* Unable to the open some already present DRM kernel module!".

I cannot find another DRM module loaded (with lsmod) and there's not DRM driver compiled into the kernel (that I could find). My configuration works perfectly when downgrading to kernel image version 2.6.10-10. A diff between the kernel image configurations and looking through the kernel image changelog did not help much either. I only found one hint: Could the newly introduced MGA DRM driver backported from 2.6.11rc1 have something to do with the problem?[/QUOTE]
 Running 2.6.10-12 I get this in the kernel messages:

[drm] Initialized drm 1.0.0 20040925

and looking at /boot/config-2.6.10-2-amd64-k8 I noticed that CONFIG_DRM=y instead of CONFIG_DRM=m. Is this ok ?
I might roll-up my own kernel using make-kpkg and changing that setting to a module and see if it makes a difference

---

### Post by Kareema on 2005-01-28
[QUOTE=Nadir]
and looking at /boot/config-2.6.10-2-amd64-k8 I noticed that CONFIG_DRM=y instead of CONFIG_DRM=m. Is this ok ?
[/QUOTE]

This is ok. In the config of kernel image version 2.6.10-10 (which is working correctly), CONFIG_DRM=y is set, too. So it shouldn't be the source of the problem.

[QUOTE=Nadir]
I might roll-up my own kernel using make-kpkg and changing that setting to a module and see if it makes a difference[/QUOTE]

If you want to make a new kernel, please try disabling DRM_MGA. The DRM_MGA module is the only new drm module introduced since the release of the last working kernel images - perhaps this makes a difference...

---

### Post by Kareema on 2005-01-28
If somebody wants to play around and compile the fglrx.ko: There are several patches available:

Patch for drivers against kernel 2.6.10 by mtippett (already in the fglrx-kernel-source AFAIK): [http://www.rage3d.com/board/showpost.php?p=1333438744&postcount=1](http://www.rage3d.com/board/showpost.php?p=1333438744&postcount=1).

Patch for drivers against kernel 2.6.11 by JonSvenJonsson (use after patch above): [http://www.rage3d.com/board/showpost.php?p=1333473014&postcount=42](http://www.rage3d.com/board/showpost.php?p=1333473014&postcount=42).

And if you want to use internal AGPGART with K8T800 chipsets you have to apply this patch by JonSvenJonsson: [http://www.rage3d.com/board/showpost.php?p=1333460154&postcount=1](http://www.rage3d.com/board/showpost.php?p=1333460154&postcount=1).

There's a thread about a fix for mtrr allocation failed/overlap error, too: [http://www.rage3d.com/board/showthread.php?t=33736241](http://www.rage3d.com/board/showthread.php?t=33736241).

---

### Post by Nadir on 2005-01-28
[QUOTE=Kareema]
If you want to make a new kernel, please try disabling DRM_MGA. The DRM_MGA module is the only new drm module introduced since the release of the last working kernel images - perhaps this makes a difference...[/QUOTE]

Hmm, if DRM_MGA is compiled as a module it shouldn't make a difference. I believe the problem is that the -11 patch includes other fixes to the basic DRM code.

On my machine, however -10 doesn't work anyway because I get an xf86_ENOSPC error in Xorg.0.log.....

Tristan

---

### Post by Nadir on 2005-01-28
A*BC*

---

### Post by daniels on 2005-01-28
I'm willing to put $5 on the -11 patch fixing the problem.

---

### Post by Kareema on 2005-01-28
[QUOTE=daniels]I'm willing to put $5 on the -11 patch fixing the problem.[/QUOTE]
Maybe, but only in a modified form. The two patch versions available in the thread are made for plain kernel 2.6.11rc: The first one can only be applied to kernel 2.6.11rc and when applied to a 2.6.10 kernel the driver doesn't compile. The second (the one I linked to in my former posting) checks the kernel versions with #ifdefs and the driver compiles correctly, but the resulting module has the same error as always.

---

### Post by Nadir on 2005-02-01
Ok, I built myself a custom kernel based on Ubuntu's 2.6.10-13. The only thing I did was changing the setting from CONFIG_DRM=y to CONFIG_DRM=m. 
 I also recompiled the fglrx module against this kernel. Now the module loads again. Here is the dmesg excerpt: 
 
  ```
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 916 MBytes.
[fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
[fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
mtrr: no more MTRRs available
[fglrx:firegl_unlock] *ERROR* Process 8907 using kernel context 0

``` 
 
 And here is what Xorg says:
 
  ```
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xffffff000012b000
(II) fglrx(0): [drm] mapped SAREA 0xffffff000012b000 to 0x2a9558c000
(II) fglrx(0): [drm] framebuffer handle = 0xe0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):	 Name: fglrx
(II) fglrx(0):	 Version: 8.8.25
(II) fglrx(0):	 Date: Jan 14 2005
(II) fglrx(0):	 Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):	 Build-Kernel UTS_RELEASE:		2.6.10.dataforte
(II) fglrx(0):	 Build-Kernel MODVERSIONS:		no
(II) fglrx(0):	 Build-Kernel __SMP__:		    no
(II) fglrx(0):	 Build-Kernel PAGE_SIZE:		  0x1000
(II) fglrx(0): [drm] register handle = 0xfb9f0000
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENOSPC"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xffffff000012b000 at 0x2a9558c000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!				  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)			 *
(WW) fglrx(0): * no 3D acceleration available			    *
(WW) fglrx(0): ********************************************* *
``` 
 
 Apart from this last error, which I am still trying to resolve, my recommendation is for the default kernel to have DRM compiled as a module.
 
 Tristan

---

### Post by Ubuntu_User on 2005-02-13
I also have everything working except DRI with a Mobility 9700. I also get the XF86_ENOSPC error. Unfortunately the BIOS on my notebook is extremely pathetic, and limited in what it lets you change. I have no options for tweaking memory settings at all, nor can I set the agpgart size (128MB default). So after strugelling with this for weeks I finally decided that the MTRR issue isn't going away, and that I should try without MTRR. So I recompiled the kernel without MTRR support, reinstalled the fglrx kernel module (recompiled for lack of MTRR) and now things work. I get about 1400fps with glxgears, other gl apps work fine. Of course this can't possibly be as fast as if MTRR was working properly but I'm at a loss for what else to try to fix the ENOSPC issue.

---

### Post by Nadir on 2005-02-16
Well, thanks to Fabio, one of these problems is solved:
 
 linux-source-2.6.10 (2.6.10-19) hoary; urgency=low
 
   * Build drm as module:
     - DRM=m.
 
 
 Thanks !!!!
 
 Tristan

---

### Post by daniels on 2005-02-16
I had a chat to one of the DRI guys tonight, and I think I know how to properly fix it, except it will be a few days before I get to it.

---

### Post by blinksilver on 2005-02-16
as long as there is a fix, and it is coming, i am happy, thanks for the good work

---

### Post by blinksilver on 2005-02-21
i checked the bugzilla report, but i thought i would ask just the same, any word on how this is coming along, my system is really hurting without 3d support

---

### Post by callahan on 2005-02-22
This all magically works for me as of today's xorg-driver-fglrx package update.  Thanks!

The machine is an Acer Ferrari with 64 bit hoary, radeon 9700 GPU.

mwc@tamale> glxgears
7679 frames in 5.0 seconds = 1535.800 FPS
7740 frames in 5.0 seconds = 1548.000 FPS
7716 frames in 5.0 seconds = 1543.200 FPS
7632 frames in 5.0 seconds = 1526.400 FPS
7708 frames in 5.0 seconds = 1541.600 FPS

I have included the relevant chunk of my xorg.conf for reference.  Note that I have not tested any changes to these options yet.  In particular I do not know if UseInternalAGPGART works with 'yes' or not, and I haven't tried undoing the mtrr option either.

  Michael


Section "Device"
    Identifier                          "Accelerated ATI"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "on" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000000"
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified"
    Option "VRefresh2"                  "unspecified"
    Option "ScreenOverlap"              "0"
# === TV-out Management ===
    Option "NoTV"                       "yes"
    Option "TVStandard"                 "NTSC-M"
    Option "TVHSizeAdj"                 "0"
    Option "TVVSizeAdj"                 "0"
    Option "TVHPosAdj"                  "0"
    Option "TVVPosAdj"                  "0"
    Option "TVHStartAdj"                "0"
    Option "TVColorAdj"                 "0"
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "no" # yes -> lockup
    Option "ForceGenericCPU"            "no"
    BusID "PCI:1:0:0"    # vendor=1002, device=4e50
    Screen 0
EndSection

---

### Post by Nadir on 2005-02-23
I got it working on my Asus A4700K too.
<HACK_ALERT>
I'm using the latest linux-image-2.6.10-4-amd64-k8 kernel with all related packages (linux-restricted-modules, xorg-driver-fglrx, linux-headers, etc)

I also got the fglrx-kernel-source package.
Went into /usr/src/modules/fglrx-kernel/fglrx/build_mod and patched firegl-public.c by replacing all occurences of the CONFIG_MTRR define with XCONFIG_MTRR so that the module thinks MTRR is not compiled into the kernel.
Went into /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x, ran make, and placed the resulting fglrx.ko in 
/lib/modules/2.6.10-4-amd64-k8/kernel/drivers/video/

Rebooted and voilà, DRI !
</HACK_ALERT>

This hack also works with the recently released ATI 8.10 drivers.
For some reason I have all MTRR registers allocated and that is why I get an xf86_ENOSPC.


 ```
$ glxgears
11681 frames in 5.0 seconds = 2336.200 FPS
11673 frames in 5.0 seconds = 2334.600 FPS
11683 frames in 5.0 seconds = 2336.600 FPS

``` 

 ```
$ fgl_glxgears
2042 frames in 5.0 seconds = 408.400 FPS
2233 frames in 5.0 seconds = 446.600 FPS
2207 frames in 5.0 seconds = 441.400 FPS
2216 frames in 5.0 seconds = 443.200 FPS
``` 

I'd rather have a <b>real</b> fix for my MTRR problem, but this works reasonably well, and it doesn't require rebuilding the entire kernel.

Tristan

---

### Post by kubla on 2005-02-23
Nadir,

I think I have virtually the same gear as you. I've got a K4774KUH... mine has the wide-screen profile and while I've got the ATI fglrx driver working, I can't get  my screen resolution up past a stretched 1024x768 (my laptop has a 16:9 widescreen profile.

Have you had any luck with it? Can you post your "Device" and "Screen" sections from your xorg.conf?

Many thanks in advance,

Ian

---

### Post by cgdef on 2005-02-24
Isn't there going to be and *official* update of the driver? It's been out for some time now...

---

### Post by Nadir on 2005-02-24
[QUOTE=kubla]
I can't get  my screen resolution up past a stretched 1024x768 (my laptop has a 16:9 widescreen profile.
[/QUOTE]

My screen is working at 1280x800 which is the default resolution (Ubuntu detected and configured it correctly).

I haven't done anything special, but here you go:

 ```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	# === disable/enable XAA/DRI ===
    Option "no_accel"				   "no"
	Option "no_dri"					 "no"
	# === misc DRI settings ===
Option "mtrr"					 "on" # disable DRI mtrr mapper, driver has its own code for mtrr
	# ### FireGL DDX driver module specific settings ###
	# === Screen Management ===
    Option "DesktopSetup"			   "0x00000100" 
	Option "MonitorLayout"			 "AUTO, NONE"
	Option "IgnoreEDID"				 "off"
	Option "HSync2"					 "unspecified" 
	Option "VRefresh2"				 "unspecified" 
	Option "ScreenOverlap"			  "0" 
	# === TV-out Management ===
Option "NoTV"					 "no"	 
	Option "TVStandard"				 "PAL-B"	 
	Option "TVHSizeAdj"				 "0"	 
	Option "TVVSizeAdj"				 "0"	 
	Option "TVHPosAdj"				 "0"	 
	Option "TVVPosAdj"				 "0"	 
	Option "TVHStartAdj"			 "0"	 
	Option "TVColorAdj"				 "0"	 
	Option "GammaCorrectionI"		   "0x00000000"
	Option "GammaCorrectionII"		  "0x00000000"
	# === OpenGL specific profiles/settings ===
    Option "Capabilities"			   "0x00000000"
	# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"			   "on"
	# === OpenGL Overlay ===
	# Note: When OpenGL Overlay is enabled, Video Overlay
	#	   will be disabled automatically
	Option "OpenGLOverlay"			  "off"
	# === Center Mode (Laptops only) ===
    Option "CenterMode"				 "off"
	# === Pseudo Color Visuals (8-bit visuals) ===
	Option "PseudoColorVisuals"		 "off"
	# === QBS Management ===
Option "Stereo"					 "off"
	Option "StereoSyncEnable"		   "1"
	# === FSAA Management ===
    Option "FSAAEnable"				 "no"
	Option "FSAAScale"				 "1"
	Option "FSAADisableGamma"		   "no"
	Option "FSAACustomizeMSPos"		 "no"
    Option "FSAAMSPosX0"			    "0.000000"
	Option "FSAAMSPosY0"			 "0.000000"
	Option "FSAAMSPosX1"			 "0.000000"
	Option "FSAAMSPosY1"			 "0.000000"
	Option "FSAAMSPosX2"			 "0.000000"
	Option "FSAAMSPosY2"			 "0.000000"
	Option "FSAAMSPosX3"			 "0.000000"
	Option "FSAAMSPosY3"			 "0.000000"
	Option "FSAAMSPosX4"			 "0.000000"
	Option "FSAAMSPosY4"			 "0.000000"
	Option "FSAAMSPosX5"			 "0.000000"
	Option "FSAAMSPosY5"			 "0.000000"
	# === Misc Options ===
    Option "UseFastTLS"				 "0"
	Option "BlockSignalsOnLock"		 "on"
	Option "UseInternalAGPGART"		 "yes"
	Option "ForceGenericCPU"			"no"
	Screen 0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
    Device		"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

---

### Post by kubla on 2005-02-24
Thanks Nadir,

I've got it now!

Now I need to resolve a problem with a webcam that works with xawtv but not gnomemeeting.

Ian

---

### Post by songochain on 2005-02-24
[QUOTE=Nadir]I got it working on my Asus A4700K too.
<HACK_ALERT>
I'm using the latest linux-image-2.6.10-4-amd64-k8 kernel with all related packages (linux-restricted-modules, xorg-driver-fglrx, linux-headers, etc)

I also got the fglrx-kernel-source package.
Went into /usr/src/modules/fglrx-kernel/fglrx/build_mod and patched firegl-public.c by replacing all occurences of the CONFIG_MTRR define with XCONFIG_MTRR so that the module thinks MTRR is not compiled into the kernel.
Went into /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x, ran make, and placed the resulting fglrx.ko in 
/lib/modules/2.6.10-4-amd64-k8/kernel/drivers/video/

Rebooted and voilà, DRI !
</HACK_ALERT>

This hack also works with the recently released ATI 8.10 drivers.
For some reason I have all MTRR registers allocated and that is why I get an xf86_ENOSPC.


 ```
$ glxgears
11681 frames in 5.0 seconds = 2336.200 FPS
11673 frames in 5.0 seconds = 2334.600 FPS
11683 frames in 5.0 seconds = 2336.600 FPS

``` 

 ```
$ fgl_glxgears
2042 frames in 5.0 seconds = 408.400 FPS
2233 frames in 5.0 seconds = 446.600 FPS
2207 frames in 5.0 seconds = 441.400 FPS
2216 frames in 5.0 seconds = 443.200 FPS
``` 

I'd rather have a <b>real</b> fix for my MTRR problem, but this works reasonably well, and it doesn't require rebuilding the entire kernel.

Tristan[/QUOTE]
Hi dude, i've a asus a4k too. Have u installed wlan?? My wlan is a sis162u and i cant install it with ndiswrapper because there isnt windows64 bit driver for sis162u yet
I've install oficial ati drivers too :D Are there any parameters to increase fps??
See u!

---

### Post by Nadir on 2005-02-25
[QUOTE=songochain]Hi dude, i've a asus a4k too. Have u installed wlan?? My wlan is a sis162u and i cant install it with ndiswrapper because there isnt windows64 bit driver for sis162u yet[/QUOTE]

I hope SIS will release 64bit drivers as soon as Windows64 is out (or sooner hopefully)

[QUOTE=songochain] I've install oficial ati drivers too :D Are there any parameters to increase fps??
See u![/QUOTE]

I don't think there is a general rule for this as I guess it is game-dependent.

nadir

---

