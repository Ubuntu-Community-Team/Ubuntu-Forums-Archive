---
title: "[SOLVED] TV capture card worked in 32 bit"
date: 2008-09-23
forum: x86 64-bit Users
---

### Post by RFXCasey on 2008-09-23
Hey all, I could really use some help with this one. Using Heron amd64 and I cannot get my capture card to work. I have a Leadtek TV2000 pro and it worked "out of the box" in the 32 bit version of Heron. I have tried TVtime and some others but they don't see the card as being installed. For instance in TVtime it says something about Konica Webcam: Invalid source or something like that. I try to change the source to my capture card but it's like it's not there. One other TV program I tried said something about no valid input device and show me something like /dev/media or something like that. I am at work so I don't remember all the details, I will post more when I get the chance. My question is how can I manually set/mnt whatever, my capture card or at least know the OS is seeing it? I could really use some help from some kind souls on this one as I don't want to have to reinstall with 32 bit as I have spent a lot of time setting up my current OS. Thanks so much for the help.:confused:

---

### Post by soxs on 2008-09-23
plx post the output from: ```
lspic
```
and check wether /dev/video or /dev/video0 exists.

---

### Post by RFXCasey on 2008-09-23
lspic didn't work so I am guessing that you ment lspci. When I type this the outup I get is.

00:00.0 Host bridge: ALi Corporation M1695 K8 Northbridge [PCI Express and HyperTransport]
00:01.0 PCI bridge: ALi Corporation PCI Express Root Port
00:02.0 PCI bridge: ALi Corporation PCI Express Root Port
00:03.0 PCI bridge: ALi Corporation PCI Express Root Port
00:04.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:05.0 PCI bridge: ALi Corporation AGP8X Controller
00:06.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:07.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:07.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:11.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
00:12.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:12.1 IDE interface: ALi Corporation ULi 5289 SATA (rev 10)
00:13.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800] (rev a1)
05:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
05:06.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
05:07.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)

Also there is a file called /dev/video0 and one called /dev/video1 but I can't look at the contents of either one. Hopefully this info will give you a clue at to what is causing the problem.:confused:

---

### Post by tjotser on 2008-09-23
05:07.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)05:07.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)

That seems to be your capture card, but how to go about installing drivers for it, i do not know.. :confused:

---

### Post by RFXCasey on 2008-09-24
I still really need help on this one so anybody who can walk through it with me would be totally appreciated. Is there a way to uninstall the card and then have Ubuntu search for new hardware and possibly set the card up again? I am pretty new to Linux but not to PCs in general. Like I said it was working in 32 bit so the problem is probably something really simple. Are there supposed to be 64 bit drivers for this card?:confused:

---

### Post by soxs on 2008-09-25
```
[ 39.045786] cx88[0]: card=0 -> UNKNOWN/GENERIC
[ 39.045788] cx88[0]: card=1 -> Hauppauge WinTV 34xxx models
[ 39.045790] cx88[0]: card=2 -> GDI Black Gold
[ 39.045791] cx88[0]: card=3 -> PixelView
[ 39.045793] cx88[0]: card=4 -> ATI TV Wonder Pro
[ 39.045795] cx88[0]: card=5 -> Leadtek Winfast 2000XP Expert
[ 39.045796] cx88[0]: card=6 -> AverTV Studio 303 (M126)
[ 39.045798] cx88[0]: card=7 -> MSI TV-@nywhere Master
[ 39.045800] cx88[0]: card=8 -> Leadtek Winfast DV2000
[ 39.045810] cx88[0]: card=9 -> Leadtek PVR 2000
[ 39.045812] cx88[0]: card=10 -> IODATA GV-VCP3/PCI
[ 39.045814] cx88[0]: card=11 -> Prolink PlayTV PVR
[ 39.045816] cx88[0]: card=12 -> ASUS PVR-416
[ 39.045818] cx88[0]: card=13 -> MSI TV-@nywhere
[ 39.045820] cx88[0]: card=14 -> KWorld/VStream XPert DVB-T
[ 39.045822] cx88[0]: card=15 -> DViCO FusionHDTV DVB-T1
[ 39.045824] cx88[0]: card=16 -> KWorld LTV883RF
[ 39.045826] cx88[0]: card=17 -> DViCO FusionHDTV 3 Gold-Q
[ 39.045828] cx88[0]: card=18 -> Hauppauge Nova-T DVB-T
[ 39.045830] cx88[0]: card=19 -> Conexant DVB-T reference design
[ 39.045832] cx88[0]: card=20 -> Provideo PV259
[ 39.045834] cx88[0]: card=21 -> DViCO FusionHDTV DVB-T Plus
[ 39.045836] cx88[0]: card=22 -> pcHDTV HD3000 HDTV
[ 39.045838] cx88[0]: card=23 -> digitalnow DNTV Live! DVB-T
[ 39.045840] cx88[0]: card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
[ 39.045843] cx88[0]: card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
[ 39.045845] cx88[0]: card=26 -> IODATA GV/BCTV7E
[ 39.045847] cx88[0]: card=27 -> PixelView PlayTV Ultra Pro (Stereo)
[ 39.045849] cx88[0]: card=28 -> DViCO FusionHDTV 3 Gold-T
[ 39.045851] cx88[0]: card=29 -> ADS Tech Instant TV DVB-T PCI
[ 39.045853] cx88[0]: card=30 -> TerraTec Cinergy 1400 DVB-T
[ 39.045855] cx88[0]: card=31 -> DViCO FusionHDTV 5 Gold
[ 39.045857] cx88[0]: card=32 -> AverMedia UltraTV Media Center PCI 550
[ 39.045860] cx88[0]: card=33 -> Kworld V-Stream Xpert DVD
[ 39.045861] cx88[0]: card=34 -> ATI HDTV Wonder
[ 39.045863] cx88[0]: card=35 -> WinFast DTV1000-T
[ 39.045865] cx88[0]: card=36 -> AVerTV 303 (M126)
[ 39.045867] cx88[0]: card=37 -> Hauppauge Nova-S-Plus DVB-S
[ 39.045869] cx88[0]: card=38 -> Hauppauge Nova-SE2 DVB-S
[ 39.045871] cx88[0]: card=39 -> KWorld DVB-S 100
[ 39.045873] cx88[0]: card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
[ 39.045875] cx88[0]: card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)
[ 39.045878] cx88[0]: card=42 -> digitalnow DNTV Live! DVB-T Pro
[ 39.045880] cx88[0]: card=43 -> KWorld/VStream XPert DVB-T with cx22702
[ 39.045882] cx88[0]: card=44 -> DViCO FusionHDTV DVB-T Dual Digital
[ 39.045884] cx88[0]: card=45 -> KWorld HardwareMpegTV XPert
[ 39.045886] cx88[0]: card=46 -> DViCO FusionHDTV DVB-T Hybrid
[ 39.045888] cx88[0]: card=47 -> pcHDTV HD5500 HDTV
[ 39.045890] cx88[0]: card=48 -> Kworld MCE 200 Deluxe
[ 39.045892] cx88[0]: card=49 -> PixelView PlayTV P7000
[ 39.045894] cx88[0]: card=50 -> NPG Tech Real TV FM Top 10
[ 39.045896] cx88[0]: card=51 -> WinFast DTV2000 H
[ 39.045898] cx88[0]: card=52 -> Geniatech DVB-S
[ 39.045900] cx88[0]: card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
[ 39.045902] cx88[0]: card=54 -> Norwood Micro TV Tuner
[ 39.045904] cx88[0]: card=55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / Swann OEM
[ 39.045907] cx88[0]: card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder

```

I think yoour card is either 5,8 or 9

To load one of the listed drivers (e.g. with card #5):
```
sudo modprobe cx88xx card=5
``` If that won't work, recheck.
If it still doesn't work, try the same with 8 and 9 instead of 5
Good Luck

EDIT: plx post the output from: ```
cat /etc/X11/xorg.conf
```

Feel free to use the thanks-button ;-)

---

### Post by RFXCasey on 2008-09-30
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Thu Feb 14 18:14:18 PST 2008

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "true"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "VX2235wm"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1680x1050"
    HorizSync       31.5 - 65.5
    VertRefresh     56.0 - 65.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Monitor"

 #                 
    Identifier     "monitor1"
    VendorName     "Generic CRT Display"
    ModelName      "Monitor 1280x1024"
    HorizSync       31.5 - 81.0
    VertRefresh     50.0 - 75.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VX2235wm"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    BoardName      "nv"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:4:0:0"
    Screen          1
EndSection

Section "Device"

 #                 
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:4:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "VX2235wm"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1400x1050@60" "1280x1024@60" "1280x960@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
    EndSubSection
EndSection

Section "Screen"

 #                 
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Virtual     1600 1200
        Depth       24
        Modes      "1280x1024@75" "1280x960@60" "1152x864@75" "1280x1024@60" "1024x768@60" "1280x960@75" "1024x768@70" "1400x1050@60" "1024x768@75" "1600x1200@65" "832x624@75" "1600x1200@60" "800x600@60" "800x600@75" "800x600@72" "800x600@56" "640x480@75" "640x480@72" "640x480@60"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP: 1440x900 +0+0; DFP: 1280x960@60 +0+0; DFP: 1152x864@75 +0+0; DFP: 1280x1024@60 +0+0; DFP: 1024x768@60 +0+0; DFP: 1280x960@75 +0+0; DFP: 1024x768@70 +0+0; DFP: 1400x1050@60 +0+0; DFP: 1024x768@75 +0+0; DFP: 832x624@75 +0+0; DFP: 1600x1200@60 +0+0; DFP: 800x600@60 +0+0; DFP: 800x600@75 +0+0; DFP: 800x600@72 +0+0; DFP: 800x600@56 +0+0; DFP: 640x480@75 +0+0; DFP: 640x480@72 +0+0; DFP: 640x480@60 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1680x1050_60 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

Like I said when I try to start TVtime it says Konica Webcam: Invalid argument  Cannot open capture device /dev/video0
The built in FM tuner isn't working either when I try to use FM radio tuner it says Could not open device /dev/radio check to make sure no other program is using /dev/radio. Also make sure you have read access to it. Hopefully I can get this straightened out.

---

### Post by soxs on 2008-09-30
> **RFXCasey said:**
> # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Thu Feb 14 18:14:18 PST 2008

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "true"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "VX2235wm"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1680x1050"
    HorizSync       31.5 - 65.5
    VertRefresh     56.0 - 65.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Monitor"

 #                 
    Identifier     "monitor1"
    VendorName     "Generic CRT Display"
    ModelName      "Monitor 1280x1024"
    HorizSync       31.5 - 81.0
    VertRefresh     50.0 - 75.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VX2235wm"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    BoardName      "nv"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:4:0:0"
    Screen          1
EndSection

Section "Device"

 #                 
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:4:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "VX2235wm"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1400x1050@60" "1280x1024@60" "1280x960@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
    EndSubSection
EndSection

Section "Screen"

 #                 
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Virtual     1600 1200
        Depth       24
        Modes      "1280x1024@75" "1280x960@60" "1152x864@75" "1280x1024@60" "1024x768@60" "1280x960@75" "1024x768@70" "1400x1050@60" "1024x768@75" "1600x1200@65" "832x624@75" "1600x1200@60" "800x600@60" "800x600@75" "800x600@72" "800x600@56" "640x480@75" "640x480@72" "640x480@60"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP: 1440x900 +0+0; DFP: 1280x960@60 +0+0; DFP: 1152x864@75 +0+0; DFP: 1280x1024@60 +0+0; DFP: 1024x768@60 +0+0; DFP: 1280x960@75 +0+0; DFP: 1024x768@70 +0+0; DFP: 1400x1050@60 +0+0; DFP: 1024x768@75 +0+0; DFP: 832x624@75 +0+0; DFP: 1600x1200@60 +0+0; DFP: 800x600@60 +0+0; DFP: 800x600@75 +0+0; DFP: 800x600@72 +0+0; DFP: 800x600@56 +0+0; DFP: 640x480@75 +0+0; DFP: 640x480@72 +0+0; DFP: 640x480@60 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1680x1050_60 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

Like I said when I try to start TVtime it says Konica Webcam: Invalid argument  Cannot open capture device /dev/video0
The built in FM tuner isn't working either when I try to use FM radio tuner it says Could not open device /dev/radio check to make sure no other program is using /dev/radio. Also make sure you have read access to it. Hopefully I can get this straightened out.

IÄll get my hands over that as soon I as I get my own one to work properly ...

---

### Post by RFXCasey on 2008-09-30
Thanks for hanging in there with me Soxs, I'll be egarly waiting to hear from you. If anyone else has any ideas please throw in your 2 cents. As I said it kind of seems like the card is not installed properly. Is there a way to reinstall it i.e. remove it and reinstall and have Ubuntu do the equivelant of "search for new hardware" or is that what the sudo modprobe cx88xx card=5for?

---

### Post by RFXCasey on 2008-09-30
Just one more thing I wanted to mention. I don't know if this applies but it is worth noting. Ever since I installed compiz-fusion if I try to reconfigure my xorg server it won't let me go throught the whole setup process. After I get to the keyboard section it dumps me out and says it overwrote a custom config and created a backup file of the old config. Kinda weird I thought. Like I said I think it started happening after my compiz-install. I did not use envy to set up my nvidia drivers I but I have the hardware drivers enabled. I don't know if any of this info will help.

---

### Post by RFXCasey on 2008-09-30
Me again. Two things I was noticing while looking through all this stuff. The first is when I did my lspci command I got
_________________________________________________________________

00:00.0 Host bridge: ALi Corporation M1695 K8 Northbridge [PCI Express and HyperTransport]
00:01.0 PCI bridge: ALi Corporation PCI Express Root Port
00:02.0 PCI bridge: ALi Corporation PCI Express Root Port
00:03.0 PCI bridge: ALi Corporation PCI Express Root Port
00:04.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:05.0 PCI bridge: ALi Corporation AGP8X Controller
00:06.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:07.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:07.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:11.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
00:12.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:12.1 IDE interface: ALi Corporation ULi 5289 SATA (rev 10)
00:13.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800] (rev a1)
05:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
05:06.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
05:07.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)

_________________________________________________________________

Now this last entry "05:07.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)" I have no idea what this is. I can only think that this my be my Leadtek Winfast 2000XP Expert capture card being detected incorrectly. Is this the card itself or is it the module that is trying to run the card? I found this link

[http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_(cx2388x](http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_(cx2388x))

Alternatively I found this information

[http://www.linuxtv.org/v4lwiki/index.php/Leadtek_WinFast_2000](http://www.linuxtv.org/v4lwiki/index.php/Leadtek_WinFast_2000)

What is bttv? Is that an alternative to cx88? I looks like it is another chipset. I have found one more post that looks like it could be useful.

[http://www.backports.ubuntuforums.org/showthread.php?t=251838](http://www.backports.ubuntuforums.org/showthread.php?t=251838)

Now lastly I would just like to ask if maybe I put the information in wrong when Sox said
_________________________________________________________________

 "I think yoour card is either 5,8 or 9

To load one of the listed drivers (e.g. with card #5):

Code:
sudo modprobe cx88xx card=5"
_________________________________________________________________

I typed in sudo modprobe cx88xx card=5

Was I supposed to plug a number into the xx part?

P.S. Please excuse my incoherent rambling. Me, thinking out loud.

---

### Post by RFXCasey on 2008-09-30
I hate to keep adding to my post but I found one more thing that my help myself and someone else if they have this issue. I'm gonna try it when i get home tonight. I will post the results.

[http://ubuntuforums.org/archive/index.php/t-789033.html](http://ubuntuforums.org/archive/index.php/t-789033.html)

---

### Post by cariboo on 2008-09-30
What is the output of:

```
dmesg | grep tuner
```

If you get something like this:

```
 dmesg | grep tuner
[   17.369813] tuner' 2-004b: chip found @ 0x96 (saa7133[0])
[   17.449021] tda829x 2-004b: setting tuner address to 61
```

you have the proper module and card setup up. If you don't you may need to try 8 and 9 for the card number.

Your tuner card won't show up in /etc/X11/xorg.conf. Install tvtime, it is available in the repositories, If you didn't get any output when you entered:

> sudo modprobe cx88xx card=5

The module installed ok and you should be able watch tv. 

Jim

---

### Post by RFXCasey on 2008-10-01
Ha Ha! I got it to work! WOOOOOOO FREAKING WHOOOOOOOOO!!!!! You guys are gonna laugh when you hear what it was. No it's not that bad. I had to unplug my (non-configured or course) USB web cam and restart the computer. Guess how I found out. I had a problem with Skype so I decided to work on setting up Ekagi. Well it was the first time I started Ekiga so it wanted me to go through the setup process. Well one of the hoops it makes you jump through is to pick a video input device. Well the first option was /dev/device0 and the second was (drumroll......) you guessed it Leadtek Winfast 2000XP Expert. Well when I was starting TV time before it was saying couldn't open Konica Webcam /dev/device0. Sooooo, I says to myself "Hey self, get off your lazy **** and climb under your desk and unplug that stupid webcam you never use. So I did and tried the TV time, this time instead of saying Konica Webcam it say something to the effect of could not locate device (I don't remember exactly). So I remembered reading that cx88 detects the device on startup. So I reboot and "BAM!" Weeeeeez in Bizniz! Worked like a charm. So them I'm like, hey why don't you try that FM tuner on that card. So I open FM radio tuner and it's like can't open device /dev/radio so I was like "Oh common!". Then I say to myself again "Hey self, why don't you look in your /dev/ directory. So thats what I do and would you believe it I have a file NOT called radio but radio0. So I restart FM radio tuner and go into the configuration and change the device to /dev/radio0 from /dev/radio and "BAM, BAM, TRIPLE FREAKIN BAM! I got glorious tunes pumping out of my speaker.....OK that's a lie it was static at first but the story sounds better the other way. I just would like to give a real heart felt thanks to Soxs, Cariboo907 and Tjoster for all your input on this and I sure hope this helps someone else in the future. I'm sure it will someday.:guitar:

---

### Post by RFXCasey on 2008-10-01
P.S. I LOVE ME SOME UBUNTU!!!!!!!!!!!!!!! Arguably the best and most configurable OS at least that I ever used. And yeah I know, "Ubuntu's not an OS!" Whatever, you know what I mean all you wiseguys out there.

---

### Post by wingnux on 2008-10-31
I have a very similar problem:

My tv card worked just fine but my webcam didn't (both connected at the same time). The webcam was set to /dev/video1 and my tv card to /dev/video0. I bought a new webcam yesterday and after plugin in it works great but now my tv card doesn't! There's only /dev/video0 (webcam) and no /dev/video1 at all!

My tv card is no. 27 on the list but I get this output:

wingnux@wingnux-desktop /dev $ dmesg | grep tuner
[   16.621733] cx88[0]: TV tuner type 59, Radio tuner type -1
[   16.858883] tuner' 2-0061: chip found @ 0xc2 (cx88[0])
[   16.859584] tuner' 2-0063: chip found @ 0xc6 (cx88[0])
[   17.091349] tuner-simple 2-0061: creating new instance
[   17.091354] tuner-simple 2-0061: type set to 59 (Ymec TVision TVF-5533MF)
[   17.132110] tuner-simple 2-0061: destroying instance


Also, it needed the following lines on /etc/modprobe.d/option in order for tvtime to get it working:

#PixelView Play TV Pro Ultra
options cx8800 video_nr=0 radio_nr=0
options cx88xx card=27 tuner=59


Any help?

Thanks in advance!

---

### Post by wingnux on 2008-11-03
Bump!

---

### Post by soxs on 2008-11-03
start a new thread, solved thread tend to not be visited that much. PM the new link.

---

