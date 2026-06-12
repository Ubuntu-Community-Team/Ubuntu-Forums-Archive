---
title: "3D Accelleration problems"
date: 2005-11-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Snipersnest on 2005-11-25
ok so I get 14,000 fps on a glxgears output. However that is with something called "Mesa" 3D libs. I can't seem to find the post I got this info on but I was wondering if anybody knew about it.

I would love to change the Mesa part over to the nvidia libs.. normally nvidia-glx fixes this but it didn't for me on the 64bit os.

If I can change to the nvidia libs I should get about 15,000 fps from glxgears and a lot smoother 3D in my games. Any ideas?

---

### Post by Snipersnest on 2005-11-26
bump....no one knows how to change the Mesa libs to the nvidia libs?

---

### Post by metoo on 2005-11-26
14000 sounds good to me?

Use synaptic -> search and search for 'nvidia'. I assume, that you have the driver from the linux-modules-restricted-yourkernel package. Actually it should have installed the nvidia-glx package (not?). May be re-install will help?

There was an update of mesa after the first release. I still haven't applied it. May be this overrun the nvidia-glx stuff. In that case just re-install the glx part.

---

### Post by RAOF on 2005-11-26
Rather than glxgears (which has the wonderful command-line switch "-iacknowlegethistoolisnotabenchmark" for printing out the fps :)), a better tool for 3D acceleration testing is "glxinfo".  For example, running that command on my system gives:
```
chris@RAOF:~/Devel/banshee$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
...

```(and much more).  The important parts being:
"direct rendering: Yes"
and
"... glx vendor string: NVIDIA Corporation".
Those two things indicate that 3D acceleration is working.  If it says "MESA" instead, that indicates that the mesa **software** OpenGL libraries are being used - no hardware acceleration.  In that case, (if you've got an nvidia card, more recent than a TNT2) you want to install the "nvidia-glx" package, and then run "sudo nvidia-glx-config enable" to switch to the nvidia drivers.

---

### Post by Snipersnest on 2005-11-28
I've done this.... nvidia-glx-config DOES NOT fix the problem...thats exactly how I installed the drivers...

---

### Post by Zimmer on 2005-11-28
Hi,
did you follow the Binary Driver instructions here?

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

I have found that these instructions on the wiki (for ATI and NVidia )
have always worked for me (but then I don't have an AMD64)

Regards

Zimmer

---

### Post by RAOF on 2005-11-28
[QUOTE=Snipersnest]I've done this.... nvidia-glx-config DOES NOT fix the problem...thats exactly how I installed the drivers...[/QUOTE]
Just to confirm, running "glxinfo" **does not** report nvidia stuff, yes?  If you've run "sudo nvidia-glx-config enable", and it still doesn't report using the nvidia gl stuff, could you post the contents of your xorg.conf and xorg.log, and maybe we can spot something obvious in there.

---

### Post by Snipersnest on 2005-11-29
Ya I'll get on that when I get off work.. I've been through my xorg.conf a ton of times now and everythings just like I had it on Hoary...But ya I'll post it.. Thanks for the help on the sound config.

---

### Post by Snipersnest on 2005-11-29
```

Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/CID"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
    Load    "opengl"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "Emulate3Buttons"    "true"
    Option        "ZAxisMapping"        "4 5"
EndSection

Section "Device"
    Identifier    "NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
    Driver        "nvidia"
    BusID        "PCI:1:0:0"
    Option "NvAGP" "2"
    Option "RenderAccel" "On"
    Option "Accel" "On"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    28-64
    VertRefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

```

---

### Post by RAOF on 2005-11-29
What is that "opengl" module doing in the modules section?  I've never seen **that** module before :confused: Maybe that's overriding your nvidia-glx module and forcing software rendering?

Here's my modules section for comparison:
```

Section "Module"
#       Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
#       Load    "dri"
        Load    "v4l"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection
```
Note no "opengl" module, and that GLCore is commented out.  This setup (a 6600GT with the nvidia drivers) glx's normally :)

---

### Post by akiro.yamamoto on 2005-11-29
I don't know if this will help but here's mine for comparision:

CODE> 
Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
.......................................
Section "Device"
	Identifier	"NVIDIA Corporation NV15DDR [GeForce2 Ti]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
EndSection


In my xorg.conf file the opengl line was remived by the nvidia driver...
I commented out the DRI section due to load error with it.
 Hope this helps you....

---

### Post by Snipersnest on 2005-11-30
[quote=RAOF]What is that "opengl" module doing in the modules section? I've never seen **that** module before :confused: Maybe that's overriding your nvidia-glx module and forcing software rendering?
[/quote]
 
That opengl thing was something I found from another post I was told to try it.. I knew it wasn't going to work but it didn't work before either..
 
Basicly my config is the same way yours is with the exception of the opengl thing....I delete the dri and glcore lines because they aren't getting used either way.
 
Any other ideas??

---

