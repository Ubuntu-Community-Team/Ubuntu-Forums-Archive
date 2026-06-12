---
title: "Monitor not recognized"
date: 2009-08-02
forum: x86 64-bit Users
---

### Post by tajreed on 2009-08-02
Acer monitor is not identified in 9.04 64 bit. Hence, can't get proper resolution. I'm using an on-board Nvidia 7025 chip with the recommended Nvidia driver with a vga input. 9.04 32 bit recognized monitor correctly with dvi cable.

Anyone have any solutions.

Thanks

---

### Post by bobince on 2009-08-04
How is the monitor described by the System->Preferences->Display program? If it's ‘Unknown’ that means the [DDC](http://en.wikipedia.org/wiki/Display_Data_Channel) is broken on your monitor (or just not coming through, which can be a dodgy cable issue; a DVI connection gets the data across differently).

You'll probably have to start messing with /etc/X11/xorg.conf maunally to tell it what resolutions to support...

---

### Post by tajreed on 2009-08-05
Any idea how I can check that or alternately how to manually configure the x.org?

---

