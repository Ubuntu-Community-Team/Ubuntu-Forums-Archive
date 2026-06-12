---
title: "Can't change CPU speed on HP Pavilion DV5"
date: 2009-06-19
forum: x86 64-bit Users
---

### Post by Th3_uN1Qu3 on 2009-06-19
I'm having a bit of trouble with power management on my laptop. I have enabled the CPU scaling monitor applet, and it never goes down from 2GHz, nor does it let me to select the speed myself (and it is running as root). I have installed powernowd, that doesn't work either. I'd really need the chip to throttle down to 1GHz when it is not in use, as the laptop gets quite hot and eats up the battery quickly.

CPU is AMD Athlon X2 QL-62.

---

### Post by Th3_uN1Qu3 on 2009-06-20
It seems to have fixed itself after a reboot. It now dynamically switches from 1 to 2GHz, and i can also switch any of the two cores manually. Perfect! :D Silly me didn't think of rebooting the machine after installing a load of stuff...

Edit: The other little thing i did before that reboot was to enable laptop mode. I guess that's what actually did the trick.

---

