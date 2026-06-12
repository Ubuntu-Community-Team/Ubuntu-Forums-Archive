---
title: "Nvidia Driver Locks up Edgy AMD64"
date: 2007-01-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Unoone on 2007-01-30
I have been having the worst nvidia driver experience with my move to Ubuntu Edgy amd64. I have tried every basic and non basic driver install method. I have even attempted some crazy fixes that worked for some others in the past. Crazy fixes like changing the agp setting in the bios to 4x when I have a 8x card. Removing the "Bios:" line from the Nvidia driver section in "xorg.conf". Messing with kernels, disabling kernels, etc, etc. :mad:

In general I have been going crazy trying to find a solution. I have swapped out a nvidia 5700 card to a 6600 card. I did bother going up another level of card. Same lockups and crashes.

All the while with each crash and boot the Nvidia logo taunts me. My reason for getting a core 2 dual Intel was for the move to Ubuntu amd64.  I'm not going to install a 32bit os on this computer.

Ok, I back where I begin, with the clean install and the Nvidia driver installs causing system lockups. Anytime the opengl functions or video acceleration is used I get lockups. The "glxinfo" command crashes my computer when acceleration is enabled on my nvidia card. I see this message i the crashed screen-

```
"name of display:0.0"
```

Before it prints out anything else the pc crashes. If I down-grade to the legacy drivers I can control 3d acceleration with these lines at the bottom of xorg.conf to experience the "glxinfo" or opengl crashes-

```
Section "Extensions"
    Option         "Composite" "Disable"
EndSection
```

I can remove these added lines in xorg.conf and reboot. Now safe from crashes I can use "glxinfo" to get this-

```
name of display: :0.0
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
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x23 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x24 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x25 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x26 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x27 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x28 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x29 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2b 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2c 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2d 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2e 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2f 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x30 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x31 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x32 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x33 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x34 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x35 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x36 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x37 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x38 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x39 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3b 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3c 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3d 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3e 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x40 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x41 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x42 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x43 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x44 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x45 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x46 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x47 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x48 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x49 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x4a 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x4b 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x4c 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x4d 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x4e 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x4f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x50 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x51 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x52 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x53 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x54 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x55 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x56 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x57 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x58 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0xd9 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault (core dumped)
```

I can't make any sense of this at all.:mad: :mad: :mad:

---

### Post by p!=f on 2007-01-30
Do you have glx extension enabled in /etc/X11/xorg.conf?
```

Section "Module"
        Load    "dbe"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        **Load    "glx"**
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

```
Be sure to have nvidia-glx and linux-restricted-modules packages installed. Check your xorg.conf (post it here if you want) for nvidia settings.
```

Section "Device"
        Identifier      "nVidia Corporation NV34 [GeForce FX 5200]"
        **Driver          "nvidia"**
        **Option          "RenderAccel"                   "true"**
        Option          "TrippleBuffer"                 "true"
        Option          "AllowGLXWithComposite"         "true"
        Option          "DisableGLXRootClipping"        "true"
        Option          "XAANoOffscreenPixmaps"         "true"
        BusID           "PCI:1:0:0"
EndSection

```

---

### Post by ehowell on 2007-01-30
I had some Nvidia problems as well, I ended up using a third party program Envy (like Automatix) which grabbed the proper drivers and installed them for you.

The original thread is here: [http://ubuntuforums.org/showthread.php?t=347107](http://ubuntuforums.org/showthread.php?t=347107)

Maybe it will work for you as well?

---

### Post by Unoone on 2007-01-31
Heres my xorg.fonf with p!=f's  suggested added Section "Device" settings -

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Mon Oct 16 22:13:48 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc101"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "altwin:meta_win"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Insignia"
    HorizSync       30.0 - 95.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS" "true"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV36.2 [GeForce FX 5700]"
    Driver         "nvidia"
    Option         "RenderAccel" "true"
    Option         "TrippleBuffer" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "DisableGLXRootClipping" "true"
    Option         "XAANoOffscreenPixmaps" "true"
    BusID          "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV36.2 [GeForce FX 5700]"
    Monitor        "Insignia"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

The glx extension is always enabled. glxgears cashes the system it freezes up like clockwork. So I can get the 3d going, it just locks up the system. The Xlib thing in "glxinfo" is a new one to me I wonder what that all means? I never saw that error until I installed Ubuntu AMD64.

---

### Post by Unoone on 2007-01-31
> **ehowell said:**
> I had some Nvidia problems as well, I ended up using a third party program Envy (like Automatix) which grabbed the proper drivers and installed them for you.

The original thread is here: [http://ubuntuforums.org/showthread.php?t=347107](http://ubuntuforums.org/showthread.php?t=347107)

Maybe it will work for you as well?

I tried it all. The drivers install real easy as always, they just don't seem to work in Ubuntu AMD64. Well for others they do just not me.:(

---

### Post by RAOF on 2007-01-31
Have you checked out the big nVidia/ATI driver thread in the Multimedia & Video forum?

[http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)

That has a link to repositories with the latest nVidia drivers nicely packaged in them.  They might be worth a try.

---

### Post by Unoone on 2007-01-31
> **RAOF said:**
> Have you checked out the big nVidia/ATI driver thread in the Multimedia & Video forum?

[http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)

That has a link to repositories with the latest nVidia drivers nicely packaged in them.  They might be worth a try.

I have used Envy, Automatix and  EasyUbuntu. These are all great apps. They get the Nvidia drivers to install all right. It's just that I'm getting system crashes "with" the Nvidia drivers installed. If I dump the Nvidia drivers and go back to the nv driver or vesa I don't get any lockups. I also don't have any 3d acceleration in Ubuntu AMD64.:mad: :mad:

---

### Post by Unoone on 2007-01-31
I'm starting to think that my problems are due to some hardware support issues beyond the Nvidia  driver.  The MBO is an 775Dual-VSTA with a VIA PT880 Pro chipset. I'm wondering if the Ubuntu amd64 OS has issues with this MBO/chipset. Maybe some of you are running Ubuntu on this great little MBO. If so, I would like to know how you configured your system and drivers.:D 

I could really use your help people, thanks.:D :D

---

### Post by kuja on 2007-01-31
It's either that (motherboard/chipset) or maybe there's a problem with the cards you've got. Brand might matter, seeing as there are quite a few manufacturers of nvidia cards. I've had good luck with eVGA, MSI, and Chaintech so far.

---

### Post by Unoone on 2007-01-31
> **kuja said:**
> It's either that (motherboard/chipset) or maybe there's a problem with the cards you've got. Brand might matter, seeing as there are quite a few manufacturers of nvidia cards. I've had good luck with eVGA, MSI, and Chaintech so far.

Yeah sometimes we venture into the great unknown. :D 

I'm using a BFG card now and tested a PNY card also, not that there's anything wrong with these.:o 

I may have to hold off from Ubuntu Edgy AMD64 for a while on this setup and come back with a new Ubuntu AMD64 release. I want to try out some new and usual, but working 64-bit Linux distros. But as always I will do everything else on Ubuntu. Maybe if we let this thread fester a bit we will come up with something in the long run. Thanks.:D

---

### Post by DocGoodbyte on 2007-01-31
> **Unoone said:**
> I have been having the worst nvidia driver experience with my move to Ubuntu Edgy amd64.

Try this thread: [http://www.ubuntuforums.org/showthread.php?t=336412](http://www.ubuntuforums.org/showthread.php?t=336412) , It has worked for me with the AMD 64  nVidia drivers.

---

### Post by Unoone on 2007-01-31
> **DocGoodbyte said:**
> Try this thread: [http://www.ubuntuforums.org/showthread.php?t=336412](http://www.ubuntuforums.org/showthread.php?t=336412) , It has worked for me with the AMD 64  nVidia drivers.

Thanks for your tip. The nvidia drivers work fine. It's just that there are some other unknown system conflicts that effect their operation in Edgy AMD64. I'm sure that these will be resolved in the future.  I just finished running an install test with Edgy 6.10 686-smp and the nvidia driver works with full 3d acceleration. More than that, the system has absolutely no lockups. 

I have experienced these type of hardware conflicts in other areas in the past installing Ubuntu. My sisters Gateway pc on board nvidia video drivers wouldn't let me install Ubuntu until the release of Edgy. Up until Ubuntu Edgy came out, any attempted install on this Gateway computer resulted in a dead black screen shortly after the cd was booted.  Well, it is a Gateway!:D

The Ubuntu developers are great at dealing with these issues, I'll leave that up to them for now.

It cost less than 500 bucks to build this 775Dual-VSTA  pc running a core 2 dual E6600 , sata drive, DDRII, and an old nasty fast Nvidia 5700 agp. In Edgy AMD64 this system is way faster than the in Edgy 686-smp.  Encoding and rendering operations went twice as fast in Edgy AMD64. Web pages loaded faster. Too bad about the nvidia driver part.  It was like that carrot in front a horse thing. Ouch!:D 

Well, I have a lot to look forward to for the next version of Ubuntu 64-bit.:D :D

Tootalu!:D

---

### Post by kleeman on 2007-01-31
You could try the nvidia forum:

[http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678)

The developers are fairly responsive although they do expect quite a bit of assistance from you.

---

### Post by Unoone on 2007-01-31
> **kleeman said:**
> You could try the nvidia forum:

[http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678)

The developers are fairly responsive although they do expect quite a bit of assistance from you.

It's ok. it's cool. I'm going to let things rest for now with Edgy AMD64. I'll get back to this later.:D

---

### Post by philipacamaniac on 2007-02-17
Other threads seem to point to a problem with the VIA PT880 Chipset:

[http://ubuntuforums.org/showthread.php?t=190341](http://ubuntuforums.org/showthread.php?t=190341)
[http://ubuntuforums.org/showthread.php?p=2168318](http://ubuntuforums.org/showthread.php?p=2168318)

I don't have any logs, though, so I don't know if a bug report would be considered.

---

