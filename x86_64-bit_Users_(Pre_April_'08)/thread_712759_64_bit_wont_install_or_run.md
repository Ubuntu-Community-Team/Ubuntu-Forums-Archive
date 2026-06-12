---
title: "64 bit wont install or run"
date: 2008-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by jombolo on 2008-03-02
Tried to install 7.10 from a cd iso. the initial menu screen appears, but when i hit enter on the first one which says something to the effect of run or install ubuntu, it briefly loads the kernel then my screen goes into power saver mode and nothing happens. i attempted a dvd iso version, same thing. does anyone have an answer? 

asus m2n-sli deluxe, 80 gig (x2) raid0, 4gig crucial ballistix, ati radeon x850 xt, amd athlon 64 x2 dual core 5200+

---

### Post by felker2 on 2008-03-02
I had the same today on a Dell Dimesion. Solution: select the second boot option from the Live-CD: "Start Ubuntu in safe graphics mode".

HTH

---

### Post by Jovec on 2008-03-02
> **jombolo said:**
> Tried to install 7.10 from a cd iso. the initial menu screen appears, but when i hit enter on the first one which says something to the effect of run or install ubuntu, it briefly loads the kernel then my screen goes into power saver mode and nothing happens. i attempted a dvd iso version, same thing. does anyone have an answer? 

asus m2n-sli deluxe, 80 gig (x2) raid0, 4gig crucial ballistix, ati radeon x850 xt, amd athlon 64 x2 dual core 5200+


See if this helps.

At the CD boot menu, press F6 to edit the command line, then modify the end of the line and replace "quiet" with "irqpoll".

If this works you'll have to modify the boot menu entry in Grub after the install.

---

### Post by marvinin on 2008-03-02
Ya. Me too. I have an AMD 64 X2 4200+, ALL-IN-WONDER X  800 XL, Asus M2N-SLI deluxe, 1 gb mem.
Tried Edubuntu 64 and same thing. Ubuntu i386 version boots up fine. Fedora 8 64 works fine too.
Tried replacing quiet with irqpoll and same thing.
Used "Start Ubuntu in safe graphics mode" and same thing.

---

### Post by Jovec on 2008-03-02
> **Jovec said:**
> See if this helps.

At the CD boot menu, press F6 to edit the command line, then modify the end of the line and replace "quiet" with "irqpoll".

If this works you'll have to modify the boot menu entry in Grub after the install.

Working from memory here... at the boot menu entry try also removing splash (and quiet) while adding irqpoll.

At the very least removing quiet and booting should give you more info.

---

### Post by studo77 on 2008-03-03
Or mybe try the alternate install cd. It worked for me, and i could not get the live-cd to work.

This option is only usable if you want to install.

The 32bit livecd did not give me any troubles.

---

