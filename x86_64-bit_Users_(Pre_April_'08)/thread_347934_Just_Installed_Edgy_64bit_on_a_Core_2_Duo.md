---
title: "Just Installed Edgy 64bit on a Core 2 Duo"
date: 2007-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Unoone on 2007-01-28
I did a fresh install and tried out some repositories beyond the basic sources.list that installed. 

Now I ran into some trouble after an update from the update panel. My system will not restart after I shut it down it just hangs and I have to refresh it. Also my Nvidia card crashes my system when I access 3d apps like Wings3d. My system even freezes when I run glxinfo in the terminal. 

I think I have to wipe it clean and reinstall. 

Is there a link for a howto or docs for Ubuntu Edgy 64bit setup? You know, repositories, 64bit drivers, etc, etc. I only see official docs for Dapper 64bit so far.

Thanks for your help.

---

### Post by Unoone on 2007-01-28
A new install with the basic sources.list. This time, Universe Nvidia-glx Drivers. Arrrrrrg! Still crashing when I use 3d apps or run "glxinfo" in the terminal. How do you tell if a driver like  Nvidia is right for Edgy 64bit? I know that for Windows XP 64bit the Nvidia website host a 64bit driver. Do I have to locate a special 64bit Nvidia driver for Edgy? Please, I need help.

Thank you.

---

### Post by Kilz on 2007-01-28
> **Unoone said:**
> A new install with the basic sources.list. This time, Universe Nvidia-glx Drivers. Arrrrrrg! Still crashing when I use 3d apps or run "glxinfo" in the terminal. How do you tell if a driver like  Nvidia is right for Edgy 64bit? I know that for Windows XP 64bit the Nvidia website host a 64bit driver. Do I have to locate a special 64bit Nvidia driver for Edgy? Please, I need help.

Thank you.

The nvidia section of [this page]("https://help.ubuntu.com/community/Video") may be of help to you. I have ati graphics so I cant give you info from experience. But you most likely want to install the proprietary video driver vs the one in the repositories.

---

### Post by Unoone on 2007-01-28
> **Kilz said:**
> The nvidia section of [this page]("https://help.ubuntu.com/community/Video") may be of help to you. I have ati graphics so I cant give you info from experience. But you most likely want to install the proprietary video driver vs the one in the repositories.

This info is for Dapper. I think that I need newer info for Edgy 64bit. And this is the method that I have used successfully to install Nvidia drivers since Ubuntu 5.04. The problem is that I am experiencing crashes on the 64bit system.

---

### Post by Kilz on 2007-01-28
> **Unoone said:**
> This info is for Dapper. I think that I need newer info for Edgy 64bit. And this is the method that I have used successfully to install Nvidia drivers since Ubuntu 5.04. The problem is that I am experiencing crashes on the 64bit system.

Your system is crashing on 3d applications, this points to a video driver problem. You may want to look for other information. But I have found that trying Dapper solutions works with common problems.

---

### Post by BIGtrouble77 on 2007-01-28
There are a couple packages that need to be installed along with nvidia-glx, like the nvidia kernel and the restricted modules.  You may want to try and install the drivers via Automatix2 ( [www.getautomatix.com](www.getautomatix.com) ).  Make sure you remove nvidia-glx and nvidia-kernel-common before you reinstall through automatix.  Do NOT remove the NV driver.

---

### Post by Unoone on 2007-01-28
Arrrrrrrrrrrg. I tried your advice Kilz.:D 

I should have known better than to listen to an ATI user.:D :D  

Actually I did my own thing and tried to install the Nvidia Drivers cold turkey from the Nvidia web site. I should have listened to the ATI user.:D  

I looked at the link you gave me and  further on down guess what, they show you how to install the same driver I downloaded from Nvidia for Ubuntu 64bit.  My system appears to be torched. In another 20 minutes I will have it reinstalled. :D 

Ahhhh,  Automatix. BIGtrouble77, in the past I have avoided this setup. But now...I'm game for anything. I want my 64bits!

Thanks people.:D 

I'll let you know if I go crawling back to my 32bit safeness.

---

### Post by Unoone on 2007-01-28
I was looking for 64bit apps in synaptic and I find almost none. I checked the repository here- 
[http://ftp.port80.se/ubuntu/pool/](http://ftp.port80.se/ubuntu/pool/)

Apps like "wings3d_0.98.35-4_amd64.deb" are not in my repositories. Hum. Is there a special repository for amd64 applications? I thought that the main, multiverse, restricted and universe in the latest web sources.list were packed with amd64 apps. What's up with this?:D

---

### Post by BIGtrouble77 on 2007-01-28
Automatix has it's own repo config.  The new version (automatix2) is MUCH better than the original script.  It's now maintained by a group of individuals and it's flawless on my machines.

---

### Post by Unoone on 2007-01-28
> **BIGtrouble77 said:**
> Automatix has it's own repo config.  The new version (automatix2) is MUCH better than the original script.  It's now maintained by a group of individuals and it's flawless on my machines.

My choice was always easyubuntu. I'll try out Automatix. "Automatix", that sounds like a cool anime character name.:D

---

### Post by kuja on 2007-01-28
!envy

...... nothing. Man, UbuntuForums needs Ubotu :D

[20:24] <ubotu> envy is a Python script that eases installation of the official Nvidia and ATI drivers. Please see [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) . Developers may be interested in [https://launchpad.net/products/envy](https://launchpad.net/products/envy) - See also !Nvidia

---

### Post by RAOF on 2007-01-29
Might I suggest you also try out !nvidia9 ?
...
<ubotu> For Ubuntu 6.10 (Edgy Eft), you can obtain the (unsupported!) 9746 version of the binary NVidia drivers by using this repository: deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable
...

---

### Post by Unoone on 2007-01-29
Here I am, back again with the same mouse freeze and screen freeze ups after a fresh install. I only added the basic Edgy repositories and installed the latest Nvidia 64bit driver with Automatix.  I looked at the threads over at - [http://www.nvnews.net/vbulletin/](http://www.nvnews.net/vbulletin/) I can't seem to get to the bottom of this. My PC freezes in this manner when I use the console entry "glxinfo". The freeze up occurs with my videos, 3d software, Nvidia settings panel, etc. Here is my xorg.conf-

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
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
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
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV36.2 [GeForce FX 5700]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV36.2 [GeForce FX 5700]"
    Monitor        "Insignia"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```

---

### Post by Unoone on 2007-01-29
I went back to the nvidia legacy drivers a got this after I uninstalled the 1.0.8776 version-


```
notme@notme-desktop:~$ glxinfo
name of display: :0.0
Error: API mismatch: the NVIDIA kernel module is version 1.0.8776, but
this library is version 1.0.7184. Please be sure that your kernel
module and all NVIDIA driver files have the same driver version.
Segmentation fault (core dumped)
notme@notme-desktop:~$ 
```

I'll try to fix this and see what happens.

---

