---
title: "[SOLVED] Setting resolution in xorg.conf"
date: 2008-08-27
forum: x86 64-bit Users
---

### Post by Plasma_NZ on 2008-08-27
ok have a new monitor, but xorg.conf keeps setting its resolution to 1440x900 when i want it to be the native 1680x1050 

what do i change in my xorg.conf to achive this..??

> 

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 640 0
    Screen      1  "Screen1" 0 0
    Screen      2  "Screen2" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Logitech G5" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
Identifier "Logitech G5" 
Driver "evdev"
Option "CorePointer"
Option "Device" "/dev/input/by-id/usb-Logitech_USB_Gaming_Mouse-event-mouse"
Option "ZAxisMapping" "invert"
Option "Emulate3Buttons" "false"
Option "Buttons" "9"
Option "Resolution" "800"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    BusID          "PCI:3:0:0"
    Screen          0
    Option     "NoLogo" "true"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    BusID          "PCI:3:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    BusID          "PCI:2:0:0"
    Option         "TVStandard" "PAL-B"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Videocard1"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
    Option         "TVStandard" "PAL-B"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard2"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 640x480 +0+0, TV: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by soxs on 2008-08-28
Do I see correct values? You are using dual 8500, one conneced with 1 display the other one with 2 ones?

---

### Post by Plasma_NZ on 2008-08-29
there's actually 4 displays connected..

2 lcd's and 2 tv'..

one tv clones one of the LCD's and the other tv runs its own xsession,
and the other 2 lcd's run there own xsessions...

i'd really like to get a 5th monitor working, but apparently vid-cards only support 2 monitors at a time...

i have since fixed the resolution problem...

---

