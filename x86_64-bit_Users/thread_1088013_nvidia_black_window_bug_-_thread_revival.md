---
title: "nvidia black window bug - thread revival"
date: 2009-03-05
forum: x86 64-bit Users
---

### Post by Youresorock on 2009-03-05
Probably everyone with an Nvidia card who has run compiz or beryl since around 7.04 knows about the Nvidia Black Window Bug.  (BWB)

There haven't been any posts on the matter in so long that the most resent is read-only.  I'm still experiencing this bug on my fully-updated 8.10 x64 machine.

I use only repo drivers, but my machine is a dist-upgrade from 8.04.

I'm rolling a 256meg Nvidia Quadro NVS 285.  Nvidia driver version reports 177.82 in the NVIDIA X Server Settings program.  I have 8GB ram.

I run into black windows every day.  I end up closing windows in order to free up video ram for new ones.  Right now I have 12 open windows, and a 13th will open black, so nothing too crazy.

Does anyone know what needs to be done to fix this?  I love compiz, and can't live without it.

---

### Post by norwoods on 2009-03-06
i download the latest releases, 180.37 currently, from [www.avenard.org](www.avenard.org).
i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev

---

### Post by istblacken on 2009-03-07
have a look at these links maybe they will help
[http://forum.compiz-fusion.org/showthread.php?t=1762](http://forum.compiz-fusion.org/showthread.php?t=1762)
[http://ubuntuforums.org/showthread.php?t=554662](http://ubuntuforums.org/showthread.php?t=554662)
[http://en.opensuse.org/Nvidia_Black_Window_Bug_Fix](http://en.opensuse.org/Nvidia_Black_Window_Bug_Fix)

---

### Post by Youresorock on 2009-03-09
Thanks for the replies.  I don't want to compile and install nvidia drivers myself as when I've done that in the past, every time there is a kernel update in the repos I have to reinstall my video drivers.  Maybe a knowledgeable person could puruse my xorg.conf and see if there is a obvious problem.  It's very vanilla, except for the the dual monitor settings.  Those were configured with the NVidia X Server Settings program.

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
# Removed Option "Xinerama" "1"
    Option         "Xinerama" "0"
EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    Identifier     "Generic Keyboard"
#    Driver         "kbd"
#    Option         "XkbRules" "xorg"
#    Option         "XkbModel" "pc105"
#    Option         "XkbLayout" "us"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    Identifier     "Configured Mouse"
#    Driver         "mouse"
#    Option         "CorePointer"
#EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 2408WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 2007WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 285"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 285"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1920+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
EndSection

```

---

### Post by Youresorock on 2009-03-26
I'm just curious, do other people not have this problem?  I expected this to be a fairly hot topic.  If you don't experience the BWB, can you post your xorg.conf?  Maybe I can figure out what's different.

---

### Post by zolek78 on 2009-03-26
Is the BWB where the desktop doesnot show anything, all i can see is a black shadow looks like the window i opened and the cursor. If it is then can some one help me to reinstall nvidia on the terminal?

---

### Post by Youresorock on 2009-03-26
> **zolek78 said:**
> Is the BWB where the desktop doesnot show anything, all i can see is a black shadow looks like the window i opened and the cursor. If it is then can some one help me to reinstall nvidia on the terminal?

Na, I think you have a different problem.  When I have a totally bogus X config I usually go to my /etc/X11 and rename the xorg.conf to xorg.bad or something.  Then restart gdm (or reboot).

This starts up X with a default config, and usually works.  you'll get 1280x1024 or thereabouts. 

The BWB is when you run out of memory with nvidia while running compiz and new windows open black.

---

### Post by nanog on 2009-04-17
Yes, I get this bug with 180.37 I have 40-50 windows open.

---

### Post by DeMus on 2009-04-18
> **nanog said:**
> Yes, I get this bug with 180.37 I have 40-50 windows open.

I didn't even know what a black window was until I started to read this thread.
With all due respect, why on earth do you have 40-50 windows open? If I have 7-8 it is a lot already: E-mail, Internet, Music, File-browser, Terminal and a program called Boinc.
I started with the 177 drivers, now i run 180.44 and as I wrote I didn't know what a black window was until now. Never experienced it.

---

### Post by punkybouy on 2009-04-18
I am using the 173 driver downloaded and installed with ENVY NG.  Running a new 9500 GT nvidia based card on a 1080P HDMI widescreen monitor at 1920x1080 resolution and am not running into any problems like yours. Do I have to open 50 windows?

---

### Post by Youresorock on 2009-04-18
I'm a web programmer, so It's not uncommon for me to have 5 nautilus, 5 terminals, 30 firefox tabs, thunderbird, open office, AIM, all open at once.  

I've just given up, and have been using unaccelerated metacity mode.  I really miss all the "expose" type features though.

Maybe I can get my boss to buy me a 512meg card.  :)

---

### Post by Youresorock on 2009-06-10
I thought I'd chime back.  Since my last post I've updated to 9.04, and still have the issue.

I ordered a 1GB 9500GT card as a workaround.  Even if the problem persists, I think I should be able to get 400% more windows before it crops up.

I attached a screenshot to help illustrate the problem.

---

### Post by cmost on 2009-06-10
I never use the drivers available in the repositories because typically they're out of date.  Get the latest drivers from nvidia's website and use those!  Be sure you have your kernel's headers installed and build-essential before you try to install them.  Basically, it's fairly simple.  I'm using 180.60 with an Nvidia 9400 GT with 512 MB RAM and have never seen a black window.  Ever!

Nvidia Drivers for x86-64:
[ftp://download.nvidia.com/XFree86/Linux-x86_64/](ftp://download.nvidia.com/XFree86/Linux-x86_64/)

If you can't be bothered to compile your own nvidia driver, then add this repository (as root) to /etc/apt/sources.list; which contains the latest nvidia drivers for Ubuntu.
deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) jaunty release

---

### Post by Arup on 2009-06-11
So far I have installed nvidia drivers via the .sh method on couple of PCs and yet to see the black window bug. I have installed, upgraded nvidia drivers myriads of times on my PC as well and never faced any issues.I am using the latest stable release 185.18.14 currently.

---

### Post by Youresorock on 2009-06-11
My 1GB 9500GT showed up.  I slapped it in and it's fantastic.  It's MUCH faster in compiz than the Quadro, and I have yet to see a black window.  Right now I have three desktops filled with tons of windows and three VMs sucking video memory and it's running fine.

I'm thinking the bug may be limited to a select few card models.  I used to have this trouble on my 7600GT at home long ago, but I don't have that card anymore.

Replacing hardware isn't really a "fix" but I'm much happier with the extra power anyway.  :D

---

