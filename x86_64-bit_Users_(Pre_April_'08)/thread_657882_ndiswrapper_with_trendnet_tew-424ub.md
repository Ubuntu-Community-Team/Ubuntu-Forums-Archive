---
title: "ndiswrapper with trendnet tew-424ub"
date: 2008-01-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2008-01-04
How is it possible to get the trendnet tew-424ub wireless usb network adapter working in Ubuntu 7.10 64 bit? Can I run a 32 bit ndiswrapper using the 32 bit Windows XP driver in a 32 bit chroot? I've looked for 64 bit drivers, but they are for Vista which doesn't work with ndiswrapper.

---

### Post by johndz on 2008-01-18
Did you get anywhere with this.  I'm in the same boat.

---

### Post by go_beep_yourself on 2008-01-19
Yeah, give me a call using voip in Linux, and I'll explain it to you. It's kind of a long complicated way to make it work, but I'm tired now and about to go to bed.

---

### Post by silver-city-productions on 2008-02-01
Me too!  What needs to be done to get the tew-424ub to work?  

This is frustrating to me; I bought this card to replace the headaches I've had trying to get a realtek rtl8185l chipset that came in my laptop to work -- my last trendnet worked with ndiswrapper with absolutely no problem, though that was on a 32bit system.

Thanks for any help!

---

### Post by go_beep_yourself on 2008-02-01
I did get it to work. You must install the software on the cd that came with the driver. That has to  be done on windows xp (not vista). Then take the .sys and .inf files that get installed some where under "Program Files" directory and use those two with ndiswrapper. This is not possible with 64 bit Linux as far as I know.

---

### Post by go_beep_yourself on 2008-02-01
With a 64 bit system, you could try the 64 bit vista drivers with wlan driverloader at [www.linuxant.org](www.linuxant.org)

---

