---
title: "Gutsy 64 + restricted drivers hangs"
date: 2007-12-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by sexus6 on 2007-12-06
Hi
I had a Feisty 64 bits install and I used nvidia restricted drivers. All was OK with that config. I updated to gutsy and the restricted drivers worked fine.

Now, for other reasons, I reinstall gutsy from zero. A clean instalation. And I have a problem.

If I use the restricted driver, the system hangs randonly. I test with some apps... first I think that flash was the problem...but no. 

With any app working, compiz disabled, the system hangs too.

I disable the restricted drivers and all works fine.

Here is my xorg.conf with restricted drivers enabled..the same that I used with feisty when all works ok::

```

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G71 [GeForce 7300 GS]"
	Driver		"nvidia"
	Busid		"PCI:7:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"LG 225WS"
	HorizSync       30-83
        VertRefresh     56-75
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G71 [GeForce 7300 GS]"
	Monitor		"LG 225WS"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
	 	Modes           "1680x1050" "1440×900" "1280×800" "1280x1024" "1280x960" "1024×768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes           "1680x1050" "1440×900" "1280×800" "1280x1024" "1280x960" "1024×768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
 		Modes           "1680x1050" "1440×900" "1280×800" "1280x1024" "1280x960" "1024×768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
 		Modes           "1680x1050" "1440×900" "1280×800" "1280x1024" "1280x960" "1024×768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
	 	Modes           "1680x1050" "1440×900" "1280×800" "1280x1024" "1280x960" "1024×768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
	 	Modes           "1680x1050" "1440×900" "1280×800" "1280x1024" "1280x960" "1024×768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 32
	 	Modes           "1680x1050" "1440×900" "1280×800" "1280x1024" "1280x960" "1024×768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by azbarcea on 2007-12-07
How do you know **nvidia** drivers are the issue?

If you use **nv** driver instead of **nvidia** is it working better? I presume that when u said:

> I disable the restricted drivers and all works fine.

you referred to **nv** dirver.

Do you have some logs?

---

### Post by sexus6 on 2007-12-07
If I disable restricted drivers from ubuntu, nv driver is working, and there is not any issue...
 the xorg.conf working is this
```

Section "Device"
	Identifier	"nVidia Corporation G71 [GeForce 7300 GS]"
	Boardname	"nv"
	Busid		"PCI:7:0:0"
	Driver		"nv"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"L225W"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1680x1050"
	Horizsync	31.5-65.5
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G71 [GeForce 7300 GS]"
	Monitor		"L225W"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1680	1050
		Modes		"1680x1050@60"	"1600x1024@60"	"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:7:0:0"
	Driver		"nv"
	Screen	1
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"	"640x480@72"	"640x480@75"	"800x600@56"	"800x600@72"	"800x600@75"	"800x600@60"	"832x624@75"	"1024x768@75"	"1024x768@70"	"1024x768@60"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"	"1792x1344@60"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```

I search through many logs: user.log, syslog, x session error. (from home)..etc... but I didn't see any error that I can identify with this issue.... but is probably that my knowledge is limited to identify this...

---

### Post by azbarcea on 2007-12-11
Be sure u have installed:

```

$ sudo apt-get install nvidia-glx-new

```

Sorry for this late answer, but try this config

```

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
#    Fontpath    "/usr/share/fonts/X11/misc"
#    Fontpath    "/usr/share/fonts/X11/cyrillic"
#    Fontpath    "/usr/share/fonts/X11/100dpi/:unscaled"
#    Fontpath    "/usr/share/fonts/X11/75dpi/:unscaled"
#    Fontpath    "/usr/share/fonts/X11/Type1"
#    Fontpath    "/usr/share/fonts/X11/100dpi"
#    Fontpath    "/usr/share/fonts/X11/75dpi"
    # path to defoma fonts
#    Fontpath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

# i'm not sure if u need all these ... but we'll give it a try
Section "Module"
    Load                "i2c"
    Load                "ddc"
    Load                "freetype"
    Load                "type1"
    Load                "glx"
    Load                "int10"
    Load                "vbe"
    Load                "GLcore"
    Load                "v4l"   
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
#    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "nVidia Corporation G71 [GeForce 7300 GS]"
    Driver        "nvidia"
    Option        "AddARGBVisuals"    "True"
    Option        "AddARGBGLXVisuals"    "True"
EndSection

Section "Monitor"
    Identifier    "LG 225WS"
    VendorName  "LG"   
    ModelName   "225WS"   
    HorizSync   30-83
    VertRefresh 56-75
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G71 [GeForce 7300 GS]"
    Monitor        "LG 225WS"
    DefaultDepth    24
    # Option         "AddARGBGLXVisuals" "True"
    SubSection "Display"
         Modes           "1680x1050" "1440×900" "1280×800" "1280x1024" "1280x960" "1024×768" "800x600" "640x480"
        Depth    16
    EndSubSection   
    SubSection "Display"
        Depth    24
         Modes           "1680x1050" "1440×900" "1280×800" "1280x1024" "1280x960" "1024×768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth 32
         Modes           "1680x1050" "1440×900" "1280×800" "1280x1024" "1280x960" "1024×768" "800x600" "640x480"
    EndSubSection
EndSection

```

What seems very weird for me is that: >  PCI:7.0.0  ... Usaully is 1, or 2 but i don't know why 7. Or why not 7. Simply I do not understand that

---

### Post by sexus6 on 2007-12-13
I made this changes... but my computer still freezing with nvidia Driver.

If I use nv driver, there is not issues, but not 3d acc.

:(

---

### Post by rsambuca on 2007-12-13
What are you doing when the computer freezes?  Is it a consistent time from boot until it freezes?

There is a memory leak with the glx-nvidia-new drivers in some setups.

---

### Post by sexus6 on 2007-12-14
> What are you doing when the computer freezes? Is it a consistent time from boot until it freezes?

It's randomly. The freeze is not associated to any program/event/time. Sometimes freezes without any reason... I make a lot of test and read a huge logs (user, syslog, etc) but I didn't see any error visible... 

The only thing that I know is that nvidia driver, with metacity or compiz freezes the computer randomly, and the nv driver not. This is with a new installation of gutsy 64.... With the same computer, in Feisty, and Gutsy upgraded from Feisty, nvidia driver works fine.

---

### Post by atila13 on 2007-12-14
I've seen that there is a problem with 64 bits architecture and 'xvinfo' program (used by 'compiz' to check 3D acceleration). 'xvinfo' resets X if you use 'nvidia' driver and 'v4l' module. If you want to use restricted driver 'nvidia', you must disable 'v4l' module.

---

### Post by jshackles on 2007-12-15
I seem to be having the same problem.  

Old setup was 32-bit Gutsy, everything was fine.  Decided to go with the 64-bit install, so I popped in a new HDD and did a fresh build.  

After enabling the restricted driver (nvidia-glx-new), my computer will hang randomly.  I also thought flash was the culpret, because it seemed to happen more often while watching YouTube.

If I disable the restricted driver, everything is fine.  I can leave my machine on overnight and it is still working in the A.M.

However, the maximum amount of uptime I've had with the nvidia driver enabled is about 20 minutes.

When it "hangs".  It seriously hangs.  Mouse / Keyboard input is not accepted, and can't find anything in the log files.  It's just that my computer literally stops working.  

Please let me know if we can find anything out about this!

---

### Post by sexus6 on 2007-12-17
> **atila13 said:**
> I've seen that there is a problem with 64 bits architecture and 'xvinfo' program (used by 'compiz' to check 3D acceleration). 'xvinfo' resets X if you use 'nvidia' driver and 'v4l' module. If you want to use restricted driver 'nvidia', you must disable 'v4l' module.

I disable this module, putting a '#' to comment the line when this module is loaded... but the freezings persist. I 'm desperate with this, I reinstall two times but the problem persist. The most weird thing is that when I update Feisty  to Gutsy all works fine, but now, with a new gutsy installation I have this problem.

I watch with my test, that when I have compiz enabled, the freezings are most frequently... with metacity freezing too, but the system last more time running.

Since Dapper I use 64 bits releases, with all the "problems" that this makes.... but now I'm thinking to change the arquithecture to 32 bits to test if this is the problem...

any suggestions?

---

### Post by azbarcea on 2007-12-17
before you begin (something I weren't paying attention)
 * To enable 3D acceleration, the GLX module needs to be activated and both the DRI and GLcore modules must be deactivated.
 * 

**First Solution**

Try with nvidia-glx dirver, or nvidia-glx-new ... Both couldn't behave the same (or shouldn't), but should work for you. I didn't understand wich driver gives you head akes, **nvidia-glx** or **nvidia-glx-new**.

So try with the first one, and afterwards, try with the second one. Both drivers are OK for your Video-Card (GeForce 7300)

**Second Solution**
something radical ... if u use kde, otherwise, do not try!

Make a backup o your ~/.kde directory, delete it and startx:
```

$ cp -fR ~/.kde ~/kde_backup
$ rm -R ~/.kde

```

Ctrl+Alt+backspace

... this will wipe ot all your settings, I just want to know if there is a kde problem or not ... u may revert anytime by replacing with your original .kde.

**Third Solution**
If problem still occours, my guess is that somthing is fishy and let's take a look through logs:
I made some research for you:

 * [http://blog.cryos.net/archives/42-System-Freezes-Caused-by-the-Proprietary-Nvidia-Driver.html](http://blog.cryos.net/archives/42-System-Freezes-Caused-by-the-Proprietary-Nvidia-Driver.html)
 * [http://gentoo.osuosl.org/distfiles/NVIDIA-Linux-x86_64-100.14.11-pkg2.run](http://gentoo.osuosl.org/distfiles/NVIDIA-Linux-x86_64-100.14.11-pkg2.run)
 * [http://gentoo-wiki.com/HOWTO_nVidia_Drivers](http://gentoo-wiki.com/HOWTO_nVidia_Drivers)


So here you should find somthing about the driver freeze ... 
```

$ sudo nano /var/log/messages

```

With all these said ... let's see what is happening ... please post here your log (regarding nvidia), your current xorg.conf, your, nvidia-driver version, your kernel version etc ... Maybe is a bug in the "nvidia-glx-new" and your are the lucky one to find it and report it :-).

---

### Post by sexus6 on 2007-12-17
> **azbarcea said:**
> before you begin (something I weren't paying attention)
 * To enable 3D acceleration, the GLX module needs to be activated and both the DRI and GLcore modules must be deactivated.

**First Solution**

Try with nvidia-glx dirver, or nvidia-glx-new ... Both couldn't behave the same (or shouldn't), but should work for you. I didn't understand wich driver gives you head akes, **nvidia-glx** or **nvidia-glx-new**.

So try with the first one, and afterwards, try with the second one. Both drivers are OK for your Video-Card (GeForce 7300)
.

Ok I'll go to follow your instructions, thanks in advance.

First Solution: Ok, I use the restricted drivers assistant from Ubuntu to enable nvidia drivers, this restricted driver installs automatically for me nvidia-glx-new, but I don't know how make this proces "manual". I have to test manually to instal nvidia-glx driver? How?

---

### Post by sexus6 on 2007-12-18
Works!!!!

The first sollution was succefully.

To change nv driver to nvidia, I use the restricted drivers manager from Ubuntu. This assistant installs nvidia-glx-new driver and enable this in the xorg.conf. I think that this manager disables the dri and glcore modules, and enables glx module.

I try to install nvidia-glx driver (not new). When this driver is active, with metacity there wasn't freezings. Suddenly if I enabled desktop effects (compiz) something was wrong. The restricted drivers manager reports me that the restricted driver needed to active compiz was not installed. I think that my manually proces to enable nvidia-glx driver didn't report to the "manager" that there is a restricted driver installed. 

For solve this, I enable normally from the restricted manager the restricted driver. This process uninstall nvidia-glx and install nvidia-glx-new. Then when driver was installed, I installed again  the nvidia-glx driver. Them, the manager was "enabled" and the correct driver that works for me, installed..

And my system are running for 20 hours and there is not freezings, with youtube, compiz and more. The problem here is that restricted manager from GUTSY, installs the new driver, and there is any bug that makes the freezings. With Feisty, restricted manager I think installs nvidia-glx drivers, noty new, and for this reason works for me when I updated the system to GUTSY, but not with a new install..

Thanks to all the people that help me, specially azbarcea
Sorry for my english

---

### Post by azbarcea on 2007-12-18
> **sexus6 said:**
> 
Works!!!!

The first sollution was succefully.



I am so thrilled! 
I think you should set this post as "solved" :-)

---

