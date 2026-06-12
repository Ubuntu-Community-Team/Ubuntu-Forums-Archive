---
title: "Transferring data from USB mass storage drops USB mouse input"
date: 2008-02-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by cdean on 2008-02-24
Lately, whenever I use a USB mass storage device (i.e. Flash drive), after transferring a few megabytes from it, my USB mouse input dies. I can still use the keyboard, however.

Nothing relevant shows in dmesg. The only way to fix it is to reboot. I've tried rmmod'ing the USB-related modules (usbmouse, *hci). Also, I generally have to use REISUB to get the system to reboot, as it hangs I think when trying to unmount the flash drive.

Relevant section in my xorg.conf:
```

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"  "Logitech USB RECEIVER"
        Option          "HWHEELRelativeAxisButtons"     "7 6"
EndSection

```
I'm obviously using evdev.

The mouse is a Logitech MX1000. The motherboard is an ASUS M3A32-MVP Deluxe/Wifi. I previously had a Foxconn C51XEM2AA with the same everything else and things worked fine.

I suspect that there could be a fix for this in the newer kernels, but this is a production system, so I can't install Hardy and would rather not roll my own kernel package.

Any pointers, folks?

---

### Post by cdean on 2008-03-09
Bump! I can't use any of my flash drives, and it happened randomly without a flash drive today.

---

### Post by cdean on 2008-03-09
OK, the randomness isn't so random: it now stops working when the screensaver comes on.

---

### Post by fjgaude on 2008-03-09
Here's what I have in my xorg.conf file, you might give such a try and see what happens:

```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device"                "/dev/input/mice"
        Option      "Protocol"              "ExplorerPS/2"
        Option      "Emulate3Buttons"       "false"
        Option      "Buttons"               "7"
        Option      "ZAxisMapping"          "4 5"
        Option      "ButtonMapping"         "1 2 3 6 7 4 5"
EndSection
```

I'm using USB mouse also.

---

### Post by cdean on 2008-03-13
Doesn't do it for me.

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ExplorerPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Buttons"       "10"
        Option          "ButtonMapping" "1 2 3 4 5 6 7 8 9 10"
        Option          "Emulate3Buttons"       "true"
EndSection

```

That's what I tried. However, I lose button functionality on my MX1000.

I also reinstalled from scratch--no dice. It's definitely a default configuration problem and not a personal configuration problem. It could also be a kernel problem. I might try a kernel recompile tonight using 2.6.24.3 or 2.6.25-rc5. It could be that 2.6.22 simply doesn't have stable drivers for the newer AMD 790X chipset.

---

