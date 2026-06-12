---
title: "Big desktop on ATI card."
date: 2009-05-02
forum: x86 64-bit Users
---

### Post by rewolff on 2009-05-02
I have an ATI 3450 graphical card. I would like to be able to use google earth -> 3D accelleration. I would also like to have a single big desktop, so that I can move windows from one monitor to the other. 

I have upgraded from intrepid-ia32 to jaunty-ia32, and then to jaunty-amd64. I had gotten "bigdesktop" to work on my ia32 setup, and all was fine. But now after upgrading to a 64 bit system, it no longer works. 

The ATI way to have one desktop is called "big desktop" it seems this cannot be enabled if xrandr is on. Turing it off according to [http://ubuntuforums.org/showthread.php?t=1129989](http://ubuntuforums.org/showthread.php?t=1129989) requires a setting in /etc/ati/amdpcsdb . The =SFALSE looks like a typo, but both options don't work.

Enabeling xinerama also doesn't work because xrandr is enabled. 

Using xrandr to configure my screens as one desktop also doesn't work. When I have my monitors working in "mirror" mode, I get to see both monitors. But getting them "next to each other" only puts them in screen-0 screen-1 mode. When I then get them in this mode, a program like grandr will show me one monitor when run on screen-0, and one monitor when run on screen-1. 

Now, I've seen pages with disturbing news that AMD hasn't upgraded their driver yet to be compatible with the X server delivered with Jaunty. And I've seen pages that claim that AMD has dropped support for older cards. I think AMD has gotten a revised driver out in time for the release of jaunty, and that my card is not old enough to have been dropped. 

When I started paying attention, I found I was running 8.6 of the proprietary AMD driver. 

On the AMD site, version 9.4 was being promoted, so I decided to upgrade manually. Due to this, I'm now apparently running 8.602. I thought I'd go to 9.4 but apparently the drivers inside the 9.4 release file have a different numbering scheme. 

Here is my current xorg.conf: 

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
        Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "Configured Video Device"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-1"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-1"
        Device     "aticonfig-Device[0]-1"
        Monitor    "aticonfig-Monitor[0]-1"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

--- 
[edit] I tried running the 32-bit X server in my 64-bit system. This freezes the system.
I tried booting the 32-bit system, and this still works.

---

### Post by coskierken on 2009-05-02
I have been working on this the past few days.  I got the big desktop, but it is still buggy.  The ATI console does not default like the 8.10(32 bit) console so you have control over multiple monitors.  I have not been able to turn on Xinerama (still working on it) and it crashes the x-server everytime I have tried.  To turn on the big desktop, you go to "System/Pref/Display" (seems odd to use the display function and not the ATI Console).  Here you can move the monitors to any configuration and not have the second as a mirror.  I have not been able to figure out, and it may not be possible with the ATI drivers att, to have different resolutions for each monitor.  When the Sharp 32" lcd is on, the max I can go on either monitor is 1350x768.  My 22" Acer can go to 1650x1050 (looks great at this res!).  I have a big destop resolution reported in the xorg.conf of 2720x768.  I have not been able to get a movie in VLC, or other movie players to put out the movie to the fullscreen to the Sharp.  I did this in 8.10(32bit) without a problem.  64-bit vid drivers for ATI are still quite buggy.  I may be switching to Nvidia very soon.  

_____________________
Q9550/MSI G45/ ATI 4650 HD/8GS 1066/WD500/HITACHI 1TB/AeroCool M40 case 
Jaunty 9.04(64)/Win Vista (64)/VMware Workstation running XP home(32bit) (inside Jaunty) to run MagicJack (yes it does work good).

---

