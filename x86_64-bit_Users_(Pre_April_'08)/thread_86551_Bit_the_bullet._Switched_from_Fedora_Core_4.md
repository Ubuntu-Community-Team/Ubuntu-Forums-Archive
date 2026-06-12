---
title: "Bit the bullet. Switched from Fedora Core 4"
date: 2005-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by linuxted on 2005-11-05
I'm impressed with 5.1 amd64.   The software support for what I want seems to be a bit better.

I do find the "sudo passwd root" thing to be wierd.

I'm also not sure my screen resolution is coming out right since it is a bit fuzzy.  I ended up monkeying with the /etc/X11/xorg.conf file...

Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX 400 AGP 8x]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-75
EndSection


It never recognized my NEC monitor like Fedora Core did (one downside).

Boot time seems good and I love new apps (open office and system to add other apps).


If anyone can help with the monitor issue I'd appreciate it.


Thanks

---

### Post by jvictor on 2005-11-06
I found that xorg gives **safe** values :) .. Y dont u just try googling ur monitor's H&V refresh rates and give them instead of the default ones ? I did that :)

---

### Post by linuxted on 2005-11-06
[QUOTE=jvictor]I found that xorg gives **safe** values :) .. Y dont u just try googling ur monitor's H&V refresh rates and give them instead of the default ones ? I did that :)[/QUOTE]

Excellent suggestion, and it worked!   Thanks so much for taking the time to help

:KS

---

### Post by wmcbrine on 2005-11-06
[QUOTE=linuxted]I do find the "sudo passwd root" thing to be wierd.[/QUOTE]
Yeah, it's weird because you're not really supposed to do that; that's more of a kludge for people like us, who are used to having a root account. Ideally, you're supposed to just sudo:

sudo vi /etc/fstab

etc. I didn't get it at first either, but now I think it's a great system. (Worst-case scenario: if you need a bunch of root operations, you can "sudo bash" and exit when done.) BTW, Mac OS X is the same way, although there, the main (first user) account also has some (IMHO) excess privileges of its own.

---

### Post by jvictor on 2005-11-06
Well i think u r posting in the wrong thread :)

---

