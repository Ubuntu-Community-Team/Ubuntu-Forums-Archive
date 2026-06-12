---
title: "Radeon 9600 X problems"
date: 2006-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by stmiller on 2006-03-25
I'm having a time getting X to display correctly. Here is my xorg.conf. I've tried commenting out certain modules (dri, and others), and tried different drivers, but no luck. the x log shows no errors.

Powermac G5 dual 2Ghz/Oct 2005
Radeon 9600 AGP
Apple Studio Display CRT 21" (Display worked fine in x86 Linux previously, 1600x1200@85; and worked with Fedora PPC using fbdev.)

Thanks for you help.

```

Section "Module"
#       Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
#       Load    "dri"
        Load    "extmod"
        Load    "freetype"
#       Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "false"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
#       Driver          "fbdev"
        Driver          "radeon"
#       Driver          "ati"
        BusID           "PCI:240:16:0"
        Option          "MonitorLayout"         "CRT,NONE"
#       Option          "UseFBDev"              "true"
#       Option          "AGPFastWrite"          "yes"
#       Option          "IgnoreEDID"            "on"
EndSection

Section "Monitor"
        Identifier      "StudioDsply2"
        Option          "DPMS"
#       HorizSync       28-90
#       VertRefresh     43-72
        HorizSync       30-107
        VertRefresh     48-120
        Modeline        "1600x1200@85"  175.50  1600 1664 1856 2160  1200 1201 1204 1250
#       Modeline        "1600x1200@75" 245.66 1600 1632 2560 2592 1200 1223 1238 1261
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
        Monitor         "StudioDsply2"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1472x1177" "1280x1024" "1272x1017" "1024x768" "960x960" "960x768" "960x720" "880x704" "832x624" "800x600" "760x608" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1472x1177" "1280x1024" "1272x1017" "1024x768" "960x960" "960x768" "960x720" "880x704" "832x624" "800x600" "760x608" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1472x1177" "1280x1024" "1272x1017" "1024x768" "960x960" "960x768" "960x720" "880x704" "832x624" "800x600" "760x608" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection
```



[IMG]http://personal.ecu.edu/stm0103/display.jpg[/IMG]

---

### Post by autocrosser on 2006-03-26
Yea--been there--done that--

I'm including my xorg.conf--running a 9600Pro 128 modded for a Dual 1.25 MDD--I've got dual monitors, so bypass that stuff--add one item at a time from my device section (I think I'd try backingstore first)

any probs--E me---

Also--you can look via terminal "man radeon" ---on login, do either Control-Option (or Apple)-F1 for a Terminal login--you get a very ugly full-screen terminal & not much else--but it's great to have as the last resort!!!!

---

### Post by stmiller on 2006-03-26
Great, thank you very much! I've attached my xorg.conf file if there are any other powermac folks out there with a stock 9600. All is working great now. Thanks again,

---

