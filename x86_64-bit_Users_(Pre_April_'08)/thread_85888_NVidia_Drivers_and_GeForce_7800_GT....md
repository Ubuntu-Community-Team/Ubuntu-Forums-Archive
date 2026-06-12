---
title: "NVidia Drivers and GeForce 7800 GT..."
date: 2005-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by homied5515 on 2005-11-03
I recently upgraded to the GeForce 7800 GT PCI-e card and a new mainboard (AMD64 Socket 939), but I'm having extreme difficulties installing / using the drivers from Nvidia's site.  I've followed the HowTo of another post, both for 5.10 Kubuntu and the 7676 version (latest) nvidia drivers.  I've finally been able to get the installer to run to completion, except for the openGL libraries, however when I edit my xorg.conf to use the "nvidia" driver instead of "nv", my boot freezes at the end of loading.  The initial Kubuntu loading screen goes basically to 100% completion (loading linux) and then freezes; instead of loading xorg and the login screen, it goes back to the text view of the boot, stalled with the most recent entries as the following:
Entering Runlevel: 2
Starting deferred execution scheduler                   [ok]
Starting periodic command scheduler                    [ok]
Checking battery state                                             [ok]
_

and the underscore is blinking, but I'm not able to enter text, just ctr+alt+del to reboot

My xorg.conf has the following modifications only:

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        [COLOR="Red"]Load    "glx"[/COLOR]
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection


Section "Device"
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "[COLOR="Red"]nvidia[/COLOR]"
        BusID           "PCI:5:0:0"
EndSection

Any advice?  I'm pretty new to debian/kubuntu, but I did manage to troubleshoot the driver installation successfully, only to have it not actually load :confused: 

cheers

---

### Post by IronWolve on 2005-11-05
NVidia 7676 appears to be broken on breezy.

---

### Post by 23meg on 2005-11-07
Which howto did you follow? Are you sure you removed the nvidia-glx package before installing?

---

### Post by tseliot on 2005-11-07
> **homied5515]I recently upgraded to the GeForce 7800 GT PCI-e card and a new mainboard (AMD64 Socket 939), but I'm having extreme difficulties installing / using the drivers from Nvidia's site.  I've followed the HowTo of another post, both for 5.10 Kubuntu and the 7676 version (latest) nvidia drivers.  I've finally been able to get the installer to run to completion, except for the openGL libraries, however when I edit my xorg.conf to use the "nvidia" driver instead of "nv", my boot freezes at the end of loading.  The initial Kubuntu loading screen goes basically to 100% completion (loading linux) and then freezes said:**
> 
Starting periodic command scheduler                    [ok]
Checking battery state                                             [ok]
_

and the underscore is blinking, but I'm not able to enter text, just ctr+alt+del to reboot

My xorg.conf has the following modifications only:

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        [COLOR="Red"]Load    "glx"[/COLOR]
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection


Section "Device"
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "[COLOR="Red"]nvidia[/COLOR]"
        BusID           "PCI:5:0:0"
EndSection

Any advice?  I'm pretty new to debian/kubuntu, but I did manage to troubleshoot the driver installation successfully, only to have it not actually load :confused: 

cheers
Follow EVERY step of my guide and if it doesn't work yet you can try the following options which you can find in the "Problems section" of my guide:

4) sudo nano /etc/X11/xorg.conf
Add the lines in red at this section of the file:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
[COLOR="Red"]Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"[/COLOR]
[COLOR="Blue"]Option "Accel" "Off"[/COLOR]
[COLOR="#ff0000"]Option "AllowGLXWithComposite" &#8220;Off&#8221;[/COLOR]

EndSection

Put the line in blue only as a last resort.

P.S. If you have any questions, please post them in the thread of my guide (see my signature for the link)

---

### Post by PenguinZdravko on 2005-11-08
> **tseliot]Follow EVERY step of my guide and if it doesn't work yet you can try the following options which you can find in the "Problems section" of my guide:

4) sudo nano /etc/X11/xorg.conf
Add the lines in red at this section of the file:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
[COLOR="Red"]Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"[/COLOR]
[COLOR="Blue"]Option "Accel" "Off"[/COLOR]
[COLOR="#ff0000"]Option "AllowGLXWithComposite" &#8220 said:**
> 

EndSection

Put the line in blue only as a last resort.

P.S. If you have any questions, please post them in the thread of my guide (see my signature for the link)
Is this works for i686 and GeForce FX 5200?
Edit: And GNOME desktop.

---

