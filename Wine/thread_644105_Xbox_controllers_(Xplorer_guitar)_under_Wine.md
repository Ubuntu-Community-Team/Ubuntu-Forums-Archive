---
title: "Xbox controllers (Xplorer guitar) under Wine"
date: 2007-12-18
forum: Wine
---

### Post by djbon2112 on 2007-12-18
I've followed the guide [here]("http://ubuntuforums.org/showthread.php?t=596347") to install my Guitar Hero 2 Xplorer USB controller. I don't know about FoF, because I don't want to use that, since I have Guitar Hero 3 PC. Now, GH3PC runs under Wine alright, but it doesn't detect the guitar. Is there anything I can/have to do to get this thing working?

---

### Post by Ferrat on 2007-12-18
what does the system say with the guitar plugged in and doing a lsusb in terminal?

---

### Post by djbon2112 on 2007-12-18
...nothing, it just hangs after entering the command. It's been ten minutes and it's just stuck there. sudo lsusb does the same thing...

Update: I rebooted my computer (without the guitar plugged in) and when it got in I did the lsusb command and got it, but as soon as I plugged in the guitar it didn't respond again. This thing worked perfectly in Windows a week ago... any ideas?

---

### Post by Dougle on 2008-01-23
I'm having a similar problem, Fret on Fire picks up the controller (had to re configure the controls in FOF options) after following this guide by Niklas Schröder:
[http://ubuntuforums.org/showthread.php?t=596347]("http://ubuntuforums.org/showthread.php?t=596347")

though the "sudo modprobe -r xpad" part hangs, i did however get it to respond at one point and got "jstest /dev/input/js0" to output the raw signal data to the screen. when it was working i tried to reconfigure the controls in Guitar Hero 3 but the controller options menu hangs completely.

Does anyone know of a way to manually edit the GH3 controls? have checked "wine regedit" and looked around the install directory.

---

### Post by JROQuinn on 2008-05-24
what about the xbox wireless guitar in wine :/ im scared to try lol

---

