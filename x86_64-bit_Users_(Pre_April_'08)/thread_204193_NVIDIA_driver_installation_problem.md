---
title: "NVIDIA driver installation problem"
date: 2006-06-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by bb7 on 2006-06-26
First I followed this guide: 
[http://www.ubuntuforums.org/showthread.php?t=133427](http://www.ubuntuforums.org/showthread.php?t=133427)

But then it said: "Ensure that Driver is set to "nvidia" and not "nv"". Mine was "nv", which made me try a lot of other stuff I found on the web. At some point I did have it working, but never saw the NVIDIA splash at startup, which I appearantly was supposed to. But now when I do the guides again ether nothing happens or it freezes at startup (until i change xorg.conf back). 

I'm running a fresh install of latest kubuntu 64. On breezy 64 and all other distros I've tried there was no probems and I'd be very happy if someone could help me :) Maybe I've removed something important when I tried to re-install... 

Some parts of my original xorg.conf:

```

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

...

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

```


EDIT: Now solved =)

---

### Post by tseliot on 2006-06-26
Try my guide:
[http://ubuntuforums.org/showthread.php?t=139264]("http://ubuntuforums.org/showthread.php?t=139264")

---

### Post by bb7 on 2006-06-27
Thanks for you reply. Unfortunatly I get the same problem afterwards. 

```

Failed to load module "glx" (a required submodule could not be loaded, 0)
Failed to load module "nvidia" (module does not exist, 0)
No drivers available

```

Parts of xorg.conf that dont work:
```

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

...

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5500]"
    Driver         "nvidia"
EndSection

```

---

### Post by tseliot on 2006-06-27
Did you try my Envy script?

---

### Post by bb7 on 2006-06-27
[QUOTE=tseliot]Did you try my Envy script?[/QUOTE]
Yes, allthough I might have missed something, but it pulled stuff down and seemed to be working fine. However at the end when it tried to start kdm (or whatever it was called I don't remember) it couldn't. And then I tried startx and got those errors in previous post.

---

### Post by tseliot on 2006-06-27
I have updated my script, please try it now (0.39)

If fixes a problem with Ubuntu 64 bit

---

### Post by bb7 on 2006-06-27
[QUOTE=tseliot]I have updated my script, please try it now (0.39)
If fixes a problem with Ubuntu 64 bit[/QUOTE]

Tried again and still no luck. It just displays the blue kubuntu logo and nothing happens until I change xorg.conf back. Maybe a re-install of kubuntu will fix it (I might have messed it up when trying everything)? Or is there any open source alternative to try out?

---

### Post by michux on 2006-06-27
[QUOTE=bb7]First I followed this guide: 
[http://www.ubuntuforums.org/showthread.php?t=133427](http://www.ubuntuforums.org/showthread.php?t=133427)

But then it said: "Ensure that Driver is set to "nvidia" and not "nv"". Mine was "nv", which made me try a lot of other stuff I found on the web. At some point I did have it working, but never saw the NVIDIA splash at startup, which I appearantly was supposed to. But now when I do the guides again ether nothing happens or it freezes at startup (until i change xorg.conf back)[...] [/QUOTE]

Try to invoke:

```
dpkg-reconfigure xserver-xorg
```

and answer the wizard's questions. It always worked for me and I got my NVIDIA card working with 3d support on an amd64 processor with Kubuntu. Hope it helps...

---

### Post by bb7 on 2006-06-30
Nah.. I'll just re-install and knock on wood. 

Thanks you two for trying =)

---

### Post by tseliot on 2006-06-30
Removing XGL might help you

---

### Post by walkerx on 2006-06-30
why not use the synaptic software, search for nvidia and then install the nvidia-glx - remember once done to start a terminal session and enter

sudo nvidia-glx-install enable

---

### Post by bb7 on 2006-07-02
I made a fresh install, updated, rebooted just in care and ran the envy script. A few errors showed up

/usr/.../extensions/libglx.so.* No such file or directory
/usr/lib/libGLcore.so.* No such...

And after saying yes to starting the xserver it printed

cat: envydm.log No such....

startex still gives the same error (no nvidia/glx modules) and I'm happy there is a backup of xorg.conf =)

Installing through adept and then "sudo nvidia-glx-install enable" don't work for me either.

---

### Post by tseliot on 2006-07-02
[QUOTE=bb7]I made a fresh install, updated, rebooted just in care and ran the envy script. A few errors showed up

/usr/.../extensions/libglx.so.* No such file or directory
/usr/lib/libGLcore.so.* No such...[/QUOTE]
This is not a problem

[QUOTE=bb7]And after saying yes to starting the xserver it printed

cat: envydm.log No such....

startex still gives the same error (no nvidia/glx modules) and I'm happy there is a backup of xorg.conf =)

Installing through adept and then "sudo nvidia-glx-install enable" don't work for me either.[/QUOTE]
Try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by bb7 on 2006-07-03
[QUOTE=tseliot]
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)[/QUOTE]

Thanks, that link was gold =) 

This is what did it for me: 
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

[QUOTE=zander]
Debian GNU/Linux or Ubuntu with Xorg 7.x
 
 If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:
 
* development tools like make and gcc are installed
 * the linux-headers package matching the installed Linux kernel is installed
 * the pkg-config and xserver-xorg-dev packages are installed
 * the nvidia-glx package has been uninstalled with the --purge option and the file /etc/init.d/nvidia-glx does not exist.
 If you use Ubuntu, please also ensure that the linux-restricted-modules packages have been uninstalled.
[/QUOTE]

---

### Post by tseliot on 2006-07-03
[QUOTE=bb7]Thanks, that link was gold =) 

This is what did it for me: 
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)[/QUOTE]
My script should do that automatically.

Do you know which step solved your problem?

---

### Post by bb7 on 2006-07-03
No unfortunatly don't know. But no pkg-config where installed, allthough that might also have been becuse of other desperate stuff I did after running the envy script...

---

### Post by drkitty on 2007-04-10
I'm also having real problems with glx / nvidia -  I've seen almost everything google will find on this.
This started after I'd upgraded ubuntu release to edgy.  I could not change the screen resolution by either using gnome's system>preferences>screen resolution) or by manually changing the xorg.conf file.  I also can't run any glx apps (e.g., glxgears) Running glxinfo I get:

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

my xorg.conf file (relevant parts):

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "Monitor"
    Identifier     "Sony SDM-S71R"
    HorizSync       20.0 - 50.0
    VertRefresh     60.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "Sony SDM-S71R"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1200x800" "1024x768" "800x600" "640x480"
    EndSubSection

relevant sections of the /var/log/Xorg.0.log are:

(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.13.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     Sony SDM-S71R (CRT-0)
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): Sony SDM-S71R (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"


(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
dlopen: /usr/lib/libGLcore.so.1: undefined symbol: _nv000040gl
(EE) Failed to load /usr/lib/xorg/modules/libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)


I've tried the following:

(1) used the envy script
(2) checked that "nvidia" not "nv" was the driver in xorg.conf 
(3) installed nvidia-glx
(4) modprobed nvidia
(5) did nvidia-glx-install enable

Now what?  Please help.
:(

---

### Post by drkitty on 2007-04-11
Ok, I did manage to get glx working by removing the restricted modules.  But, still can't force the nvidia driver to provide the resolution /  refresh options I know the monitor is capable of.

---

