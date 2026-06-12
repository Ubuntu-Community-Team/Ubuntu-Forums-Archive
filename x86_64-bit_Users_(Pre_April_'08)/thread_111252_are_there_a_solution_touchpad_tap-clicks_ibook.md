---
title: "are there a solution: touchpad tap-clicks ibook?"
date: 2006-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by berndTosh on 2006-01-01
hi all.

I have installed Ubuntu 5.10 on an 12" ibook G4 and fixed a lot off things.
Only the touchpad make me crazy. Everytime when I write a text i make some clicks on the touchpad.

i search a lot in web and edit my /etc/X11/xorg.conf

> Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "yes"
EndSection

syndaemon also, get everytime this message bellow

> 
root@godezilla:~# syndaemon 
Can't access shared memory area. SHMConfig disabled?


(evdev run)

ksynaptics is installed but dont no how do start...

but all tips i found i doesnt work on my box.

The best way for me i think is to disable the clicking on the touchpad.

Get anyone a solution on it?

---

### Post by lusepuster on 2006-01-03
Install Mouseemu. That will automagically disable the trackpad while typing and until some time later. NB: Mouseemu will shift your middle- and right click fom F11 and F12 to F10 and F11.
Mouseemu also lets you scroll by holding down the ALT-key and sliding your finger on the trackpad. Mouseemu is enabled as soon as installed.

Alternatively you can install PowerPrefs (a graphical front-end to pbbuttonsd), but they do recommend that you use Mouseemu for the purpose.

---

