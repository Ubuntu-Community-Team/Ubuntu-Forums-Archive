---
title: "usb printer detection"
date: 2009-05-06
forum: x86 64-bit Users
---

### Post by j0eb0b on 2009-05-06
I am having a problem detecting a printer using Jaunty.  It previously was detected without issue using 8.04.  The printer in question is an older HP Laserjet 5l that is connected to the system via a parallel to usb cable since the printer was made to be attached to a parallel MB port.  Modern motherboards no longer include a parallel port.  The Jaunty printer setup menu detects an"Unknown" printer on the system.  Any ideas how to get this working?

Additionally, I have a Canon Pixma IP 1600 connected via usb which is properly identified.  There are, however, no drivers in the printer set-up for this device.  Any idea where to find one or a generic driver that may work? Canon apparently does not provide linux device drivers, of at least I haven't been able to find any.

---

### Post by Arup on 2009-05-06
Good luck with Canon, have been begging for drivers for my IP6210D since 2006, no go, have to use Turbo print drivers but they are costly. This will be my first and last Canon ever. [www.turboprint.info/](www.turboprint.info/)

---

### Post by dcstar on 2009-05-08
> **j0eb0b said:**
> I am having a problem detecting a printer using Jaunty.  It previously was detected without issue using 8.04.  The printer in question is an older HP Laserjet 5l that is connected to the system via a parallel to usb cable since the printer was made to be attached to a parallel MB port.  Modern motherboards no longer include a parallel port.  The Jaunty printer setup menu detects an"Unknown" printer on the system.  Any ideas how to get this working?


Do you have the **hplip & hpoj** packages installed?

---

