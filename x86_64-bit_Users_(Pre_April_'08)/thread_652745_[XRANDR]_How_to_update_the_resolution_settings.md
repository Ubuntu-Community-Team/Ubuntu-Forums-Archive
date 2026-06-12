---
title: "[XRANDR] How to update the resolution settings?"
date: 2007-12-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by boppp on 2007-12-29
Today I installed the new ATI drivers, just got sum little problems, maybe someone can help me out:
```

bob@bob-laptop:~$ uname -a
Linux bob-laptop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
bob@bob-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.1.7170 Release

```


I got a laptop with a TFT monitor plugged in, so sometimes i want to use the TFT and sometimes my Laptop (never at the same time), my laptop is max. resolution 1280x800 and the TFT is 1680x1050 (i read about the known issue).

But when i switch to my TFT screen with the following command line:
```

aticonfig --enable-monitor=tmds1 && \
xrandr -s 0

```

Output at that moment of xandr is:
```

bob@bob-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0* 
   1024x768       60.0     75.0     72.0     70.0  
   800x600        60.0     75.0     72.0     70.0     56.0  
   640x480        60.0     75.0     72.0  
   640x400        60.0     75.0  
   512x384        60.0     75.0  
   400x300        60.0     75.0  
   320x240        60.0     75.0  
   320x200        60.0     75.0  

```

Well, the first thing is, no larger then 1280x800, but even more strange is that it is the EXACT same output as my laptop screen gives. It almost looks like xrandr doesnt look for any changes. Does anyone know how i can make xrandr update the resolutions of my ftf or where xrandr gets them from?

Below the relative part of xorg.conf

Edit:
```

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[1]"
        HorizSync    30.0 - 81.0
        VertRefresh  56.0 - 75.0
        ModeLine     "1680x1050" 146.2 1680 1784 1960 2240 1050 1053 1059 1089 -hsync -vsync
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "EnableMonitor" "lvds"
        Option      "DesktopSetup" "single"
        BusID       "PCI:1:0:0"
EndSection
Section "Device"
        Identifier  "aticonfig-Device[1]"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1280x800"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[1]"
        Device     "aticonfig-Device[1]"
        Monitor    "aticonfig-Monitor[1]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1680x1050"
        EndSubSection
EndSection

```

---

### Post by boppp on 2007-12-30
sorry for the kick, but i really would like some nice resolution on my screen ;)

---

