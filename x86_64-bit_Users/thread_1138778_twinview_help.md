---
title: "twinview help"
date: 2009-04-26
forum: x86 64-bit Users
---

### Post by zip_000 on 2009-04-26
Hello everyone.

I know that there are a tone of twinview walkthroughs out there, but nothing that I've tried will work. Here's my set up:
64bit Ubuntu 9.04
Nvidia 9800 GT
1 wide screen monitor [connected via dvi]
1 old tube tv [connected via s-video]

Here's my xorg.conf:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "DontZap" "False"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
	# generated from default
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor"
    VendorName     "Unknown"
    ModelName      "HSD JW197D"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HSD JW197D"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option         "UseEdidFreqs" "True"
    Option         "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
    Option         "UseDisplayDevice" "TV"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "G92-200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen"
    Device         "Device"
    Monitor        "Monitor"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "NoTwinViewXineramaInfo"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, TV: nvidia-auto-select +1440+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

I really can't see why this doesn't work. I've used nvidia-settings to create this file, and the settings manager shows things looking the way that should. I've tried just about everything I could find, but nothing is working.

This is all on a new computer; all of this worked fine on my old computer. So far the only thing that I can get to work is separate x screens with xinerama. This works ok, but I see (at least) 2 problems:
1) I can't turn it on and off whenever I want so the only way to get the tv back to cable is to unplug the s-video.
2) Composite effects don't work.

Any help would be greatly appreciated!

---

### Post by zip_000 on 2009-04-27
Would this be better in one of the other forums?

If an administrator sees this and thinks it would get more help elsewhere, please feel free to move it! It doesn't seem to really be a 64bit problem, but I am running the 64bit version of the OS and Nvidia driver.

To clarify an earlier point, in nvidia-settings it shows things looking correct: it shows the primary monitor (1440x900) and it shows the tv (1024x768) immediately to the right of the main monitor. Under configure, it says that it is set to "twinview." But there is nothing on the TV. I'm beginning to think that there is something odd with the graphics card it is the XFX NVIDIA GeForce 9800 GT:
[http://www.xfxforce.com/en-us/products/graphiccards/9series/9800GT.aspx](http://www.xfxforce.com/en-us/products/graphiccards/9series/9800GT.aspx)

The TV out(s-video) does work in Windows though, so it does work.

I'm really rather frustrated with this problem.

Thanks!

---

