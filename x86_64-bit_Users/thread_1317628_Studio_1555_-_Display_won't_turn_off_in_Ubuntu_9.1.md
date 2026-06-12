---
title: "Studio 1555 - Display won't turn off in Ubuntu 9.10"
date: 2009-11-06
forum: x86 64-bit Users
---

### Post by nishant.singh28 on 2009-11-06
I have a Studio 1555 with Karmic 64 bit. The display does not go off by itself even when I have configured it to switch off after 5 minutes. I tried editing my xorg.conf file ad it now looks like this:
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Option           "OffTime" "3"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-LCD"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1366x768"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-LCD" "0-LCD"
    BusID       "PCI:1:0:0"
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

Killing gnome power manager is not an option as I frequently have to run my notebook on battery and I need the battery charge status from gnome power manger. When I run the command :
xset -display :0 dpms force off

This is the only command that manages to switch the display off and keep it so. NO other command keeps the LCD off for more than a minute.
Please help!!!!!!!!!!

---

### Post by nishant.singh28 on 2009-11-07
It turns off normally but won't do so if there is music running in the background and I want it to turn off if there's just music in the background

---

### Post by Sergio PC on 2009-11-10
Ya, I have the same problem, I use xset -display :0 dpms force off But after a couple of seconds the screen will turn back on, this didn't happen in Juanty. R400 Thinkpad 64bit Karmic.

---

### Post by nishant.singh28 on 2009-11-10
Switched to Amarok 1.4 (2 is crappy :confused: ) problem solved :D

---

### Post by alexcabal on 2009-11-11
I'm getting the same problem on my vanilla Dell Vostro 1400.  Since Intrepid I've used 

$> xset dpms force off 

to shut down my laptop screen when I want to save power.  No problems until Karmic--now the screen shuts down, but after a few seconds, it turns back on again, even if there's no activity.  Anybody have any ideas?

---

### Post by alexcabal on 2009-11-12
Just an update--I may have fixed the problem on my laptop.  I went to the Power Management dialog and unchecked the 'dim display when idle' box, then set 'put display to sleep when inactive for' to 'never' on both AC and battery.  Now the command seems to keep the display off as usual.

---

### Post by DGMcCloud on 2009-11-17
I have the same problem on a Dell D820. alexcabal's fix/workaround doesn't seem to work on my machine.

---

