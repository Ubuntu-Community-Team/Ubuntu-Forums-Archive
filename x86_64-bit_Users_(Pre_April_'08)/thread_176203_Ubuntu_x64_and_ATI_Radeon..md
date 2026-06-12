---
title: "Ubuntu x64 and ATI Radeon."
date: 2006-05-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kubikas on 2006-05-14
Hello,
First of all i have, AMD64 Athlon 3000+, 2gb ram, and ATI Radeon X1300PRO.
I had problem with "starting hotplug subsystem", because it hanged the installation, but I clicked ctrl+c, and disabled intel_agp in blacklist, but now i have problem, that X11 can't start, because it detects "no screens", in fact in log file, i can't see the model drivers for it. Any suggestions?

Kubikas

---

### Post by skylark on 2006-05-15
you might have lucked out badly here... my understanding is that the X.org radeon drivers don't support the X1300 and the official ATI drivers don't either! The only way to get you system working might be to use the "vesa" driver (not ideal but at least it should work).

To do this change the driver section in /etc/X11/xorg.conf to "vesa". For example:```
Section "Device" 
Identifier "ATI Technologies, Inc. ATI Default Card" 
Driver "vesa" 
BusID "PCI:1:0:0" 
EndSection
```
You can use the "nano" text editor to do this (type: sudo nano /etc/X11/xorg.conf)

---

### Post by Kubikas on 2006-05-15
Thanks, I'll try that ;-) already figured, that no ati drivers exist.

ps.: i prefer `vi` ;-)

---

### Post by Kubikas on 2006-05-15
Worked perfectly with 1280x1024@24, thank you again.

---

