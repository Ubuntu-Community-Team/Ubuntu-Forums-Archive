---
title: "Help with Beryl"
date: 2006-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by thoffland on 2006-10-13
I'm on Dapper 64 and cannot seem to get it to install. I installed it a couple of weeks ago on my laptop (didn't have enough juice) and now it wont install. I've tried a bunch of the guides, but I'm getting this error: 

```
$ sudo aptitude install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald-themes
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find package "beryl".  However, the following
packages contain "beryl" in their name:
  beryl-plugins-data
The following packages are BROKEN:
  emerald-themes
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1292kB of archives. After unpacking 3207kB will be used.
The following packages have unmet dependencies:
  emerald-themes: Depends: emerald (>= 0.1) which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

```

I'm sure it doesn't matter at this point, but here's my xorg.conf too: 

```

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
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

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

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
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
    Identifier     "DELL 2005FPW"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "DELL 2005FPW"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection


```

I'm hoping it's just that the repository is down temporarily??

---

### Post by xpod on 2006-10-13
i installed it all last night mate but i just sort of stumbled along and cant recall what i followed but i got the beryl settings manager and the emerald theme manager there and ive added all the relevant scripts and repos and lines to files blah blah blah...........

And it still dont seem to work:mrgreen: ...Im using a new nvidiagforce mx4000
and its all installed and working......apparently:D 

I feel for you mate ...but the best is yet to come....lol

EDIT:..this is what i used m8
[http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)

PS..I found another guide  suggesting we need to enter a few lines in the "xorg.conf" just at the nvidia "device" section so i`ll try track it down again...im sure i had tried it but upon checking my file its still the same as yours.....ish

Sorry i forgot your not even that far yet.......the repo`s should be ok as long as you have added them to your sources list....try this guide

---

### Post by thoffland on 2006-10-13
Thanks for the tip, I tried that and it's not working. Here's the errors I'm getting for installing emerald, and beryl-manager: 

```
thoffland@Whoopass:~$ sudo apt-get install xserver-xgl compiz-gnome emerald emerald-themes beryl
Reading package lists... Done
Building dependency tree... Done
xserver-xgl is already the newest version.
Package emerald is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package emerald has no installation candidate
thoffland@Whoopass:~$ sudo apt-get install beryl-manager
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package beryl-manager

```

:-k

bummer, I really would like to get it working, I'm so curious. Thanks for the help, I appreciate it!

---

### Post by thoffland on 2006-10-21
Ok, I got it working thanks to the patience of killkoy. Here's the link: 

The howto:
[http://ubuntuforums.org/showpost.php?p=1641521&postcount=35](http://ubuntuforums.org/showpost.php?p=1641521&postcount=35)

From this thread: 
[http://ubuntuforums.org/showthread.php?p=1641521#post1641521](http://ubuntuforums.org/showthread.php?p=1641521#post1641521)

---

