---
title: "adjusting touchpad sensitivity"
date: 2009-07-19
forum: x86 64-bit Users
---

### Post by seabiscuit on 2009-07-19
Hi,

I am running ubuntu 64 bits and I had a "sensitivity problem" with my touchpad: basically while writing docs the mouse pointer was jumping all over the place beause of too much sensitivity.

Currently I used System-->Preferences-->Mouse 

and disabled from there the touchpad.

I would very much appreciate your help with tecahing me how to make the touchpad less sensitive as opposed to totally disable it.

Thank you very much anticipated.

PS: I am still using my mouse now, the problem is the touchpad

---

### Post by devildoc5 on 2009-07-20
ok well I am not sure if this would help as I generally use my touchpad and have not had this problem before.......  

But there is a setting when you open up System>Preferences>Mouse under the General tab that has acceleration and sensitivity sliders.  I do not know however if this would solve your problem or just make your actual mouse really slow and unresponsive.......

---

### Post by seabiscuit on 2009-07-21
> **devildoc5 said:**
> ok well I am not sure if this would help as I generally use my touchpad and have not had this problem before.......  

But there is a setting when you open up System>Preferences>Mouse under the General tab that has acceleration and sensitivity sliders.  I do not know however if this would solve your problem or just make your actual mouse really slow and unresponsive.......

Thank you 
                                  [devildoc5  ]("http://ubuntuforums.org/member.php?u=751894")

for your reply.

Unfortunately employing the strategy you've suggested either heavily impared my mouse (if i choose extreme settings) or does not reduce enough the sensitivity of the touchpad ...

any other solution?

Thank you very much.

---

### Post by devildoc5 on 2009-07-21
well I am sorry that did not work for you......let me see if I got a usb mouse around here somewhere I can plug in and see what I can figure out for you.

---

### Post by devildoc5 on 2009-07-21
ok I found something out from an old post......I do not know how "brave" you are feeling but you can always edit the /etc/X11/xorg.conf file.  Make sure that you have a "touchpad" setting and a "mouse1" setting or two mouse settings before executing this edit.

MAKE SURE TO BACKUP YOUR xorg.conf FILE FIRST!

```

sudo gedit /etc/X11/xorg.conf

```

then do a search for "touchpad" and it SHOULD bring up a place that will look sort of like this:

```

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig"        "on"
EndSection

```

After the SHMConfig line you are going to add the following:

```

Option		"MinSpeed"		"1.0"
Option		"MaxSpeed"		"1.3"
Option		"AccelFactor"		"0.3"

```

and adjust the numbers to whatever personal tastes you have.  Also you may need to make sure that your other mouse is showing up inside of the xorg.conf as well.  It should be listed as "Mouse1" or something to that affect.

If not you are going to have a lot more fun, but just post here and I will walk you through it.

Make sure after you have applied the changes to xorg.conf and saved it, that you log out and log back in to apply the changes.

Like I said if you do not have your mouse AND your touchpad listed in your xorg.conf DO NOT edit until you let me know and we can add some more code to your xorg.conf.

---

### Post by seabiscuit on 2009-07-22
> **devildoc5 said:**
> ok I found something out from an old post......I do not know how "brave" you are feeling but you can always edit the /etc/X11/xorg.conf file.  Make sure that you have a "touchpad" setting and a "mouse1" setting or two mouse settings before executing this edit.

MAKE SURE TO BACKUP YOUR xorg.conf FILE FIRST!

```

sudo gedit /etc/X11/xorg.conf

```then do a search for "touchpad" and it SHOULD bring up a place that will look sort of like this:

```

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig"        "on"
EndSection

```After the SHMConfig line you are going to add the following:

```

Option        "MinSpeed"        "1.0"
Option        "MaxSpeed"        "1.3"
Option        "AccelFactor"        "0.3"

```and adjust the numbers to whatever personal tastes you have.  Also you may need to make sure that your other mouse is showing up inside of the xorg.conf as well.  It should be listed as "Mouse1" or something to that affect.

If not you are going to have a lot more fun, but just post here and I will walk you through it.

Make sure after you have applied the changes to xorg.conf and saved it, that you log out and log back in to apply the changes.

Like I said if you do not have your mouse AND your touchpad listed in your xorg.conf DO NOT edit until you let me know and we can add some more code to your xorg.conf.

Hi devildoc5,

Given your explicit instructions (thanks a lot for taking your time!!!) I felt "brave" and wanted to go ahead and do what you suggested.

However my xorg.conf does not have the section you mentioned. Consequently I am respecting your instructions and hold here...

I would appreciate your help with adding the suplementary code.

Please see below my current xorg.conf file:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Thank you!

---

### Post by devildoc5 on 2009-07-22
wow....that xorg has absolutely nothing in it at all...... the basics that I can gather from what I see of your system and from wehat you have told me is that there is not a seperate input for your touchpad and your mouse.....for some reason ubuntu is reading these as the same device.

Do me a favor and run this in a terminal:
```

lspci

```

and post that up here.  With both the touchpad active and the external mouse plugged in if you can......

---

### Post by seabiscuit on 2009-07-23
> **devildoc5 said:**
> wow....that xorg has absolutely nothing in it at all...... the basics that I can gather from what I see of your system and from wehat you have told me is that there is not a seperate input for your touchpad and your mouse.....for some reason ubuntu is reading these as the same device.

Do me a favor and run this in a terminal:
```

lspci

```and post that up here.  With both the touchpad active and the external mouse plugged in if you can......

devildoc5: apologies for the delay, i was not able to check the board in the last 24 hrs.

Please see below the output of the command lspci as you requested:

lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

---

### Post by devildoc5 on 2009-07-25
ok sorry, been working 18 hours days these last few days, regrettably the forums were the last thing on my mind when I got home.

It appears from what you post that your touchpad is a usb device so i am going to need to to also run a: lsusb

and post that here as well..... I am trying to track down how it is recognizing each of your devices, both the mouse and the touchpad.....  That should help us come to a resolution......


Also, I am scheduled to work another twelve hours tomorrow, which will probably turn into 18 or 20.......It may not be until sunday afternoon until I can look at this post again.....

---

### Post by seabiscuit on 2009-08-02
Please see below the output from lsusb (hope u got some rest)

> lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 007 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 007 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by seabiscuit on 2009-08-04
Any suggestion about how to fix this anoying touchpad sensitivity issue? Please see the earlier posts of this thread for background.

thank you very much!

---

### Post by devildoc5 on 2009-08-06
ok well I am not seeing where your touchpad is connected at, so I am unable to help you to add the correct code into you xorg.conf

I apologize for my lack of further knowledge.  Perhaps someone else will be able to come along with a little bit more knowledge than myself to be able to complete this problem and help you fix it.

---

### Post by seabiscuit on 2009-08-06
> **devildoc5 said:**
> ok well I am not seeing where your touchpad is connected at, so I am unable to help you to add the correct code into you xorg.conf

I apologize for my lack of further knowledge.  Perhaps someone else will be able to come along with a little bit more knowledge than myself to be able to complete this problem and help you fix it.

devildoc5: thank you very much for your kind attempts to help me.

Anybody else has any idea about how can I get out of this mouse (touchpad) trap?

Thanks

---

### Post by HotShotDJ on 2009-08-06
Try disabling just the tap to click feature.  It won't prevent you from accidentally moving the cursor, but it will prevent actually moving the insertion point while you type. (You'll find this in Mouse Preferences under the "Touchpad" tab)

Of course, the BEST fix is to adjust your typing style.  If you are accidentally rubbing a your palm or wrist across the touch-pad whilst typing, then you must be holding your hands in a very awkward manner.  Your fingers should always be hovering above the "home keys" with thumbs hovering over the "space" bar.  Your wrists should be firmly resting on either side (not over) the touch-pad.  This will maintain your wrists in a straight position relative to your lower arm and palm. Hovering your wrists above the touch-pad, as you must be doing, can result in carpal tunnel syndrome -- definitely NOT fun.

---

### Post by del_diablo on 2009-08-06
> Of course, the BEST fix is to adjust your typing style. If you are accidentally rubbing a your palm or wrist across the touch-pad whilst typing, then you must be holding your hands in a very awkward manner. Your fingers should always be hovering above the "home keys" with thumbs hovering over the "space" bar. Your wrists should be firmly resting on either side (not over) the touch-pad. This will maintain your wrists in a straight position relative to your lower arm and palm. Hovering your wrists above the touch-pad, as you must be doing, can result in carpal tunnel syndrome -- definitely NOT fun.

I have disabled my own touchpad because i was to lazy to find a way to disable "hit twice equals a mouse click", on my laptop its about impossible to not hit it randomly once in a while.
Well, a touchpad that the double tapping is disabled would be very nice(it would actually make it possible to play RTS or FPS games with it).

---

### Post by seabiscuit on 2009-08-06
> **HotShotDJ said:**
> Try disabling just the tap to click feature.  It won't prevent you from accidentally moving the cursor, but it will prevent actually moving the insertion point while you type. (You'll find this in Mouse Preferences under the "Touchpad" tab)

Of course, the BEST fix is to adjust your typing style.  If you are accidentally rubbing a your palm or wrist across the touch-pad whilst typing, then you must be holding your hands in a very awkward manner.  Your fingers should always be hovering above the "home keys" with thumbs hovering over the "space" bar.  Your wrists should be firmly resting on either side (not over) the touch-pad.  This will maintain your wrists in a straight position relative to your lower arm and palm. Hovering your wrists above the touch-pad, as you must be doing, can result in carpal tunnel syndrome -- definitely NOT fun.

How can I adjust my typing file? I would appreciate (a pointer to) instructions.

---

### Post by HotShotDJ on 2009-08-06
> **seabiscuit said:**
> How can I adjust my typing file? I would appreciate (a pointer to) instructions.No, no, no.  You've misunderstood (I think).  There is no typing file.  I suggested that you adjust your typing **STYLE**.  Its about how your fingers, thumbs, palms, and wrist are positioned. Re-read the second paragraph of my previous post to this thread for the instructions.

It may feel odd when you first start doing it.. and it may even slow down your typing at first.  But with practice, it should start feeling quite natural and your typing speed will pick up and likely over take your previous speed.

---

