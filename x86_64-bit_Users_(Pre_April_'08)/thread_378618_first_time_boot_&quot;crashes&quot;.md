---
title: "first time boot &quot;crashes&quot;"
date: 2007-03-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by luekthahoagieman on 2007-03-07
linux noob here just downloaded ubuntu self install/play cd for "6.10 desktop amd64" version.  already have XP (*shudders*) and restart to boot from said disc.  successfully checked cd for errors and let memory test run for about 10 hours( 14 passed tests, i don't know if i should have kept going....).  Trying either normal or 'safe-graphics' mode, i eventually receive an "x-server" error.  more specifically:

    Build OS: linux 2.6.15.7 x86_64
Current OS: linux ubuntu 2.6.17-10-generic #2 SMP

(==) Log File: "/var/log/Xorg.0.log"
(==) Using config file: "/etc/X11/Xorg.conf"
(EE) No devices detected.

         fatal server error
            no screens found

---

### Post by I'm_pissed on 2007-03-07
I have the same problem

hardware:
ASUS K8N4-E Deluxe
ATI Radeon X800 GTO on PCI Express

PS I'm not really pissed

---

### Post by bryan.taylor on 2007-03-07
Every time I've gotten that error it's been because my graphics driver failed to initialize.  Try a different graphics driver?  Go with "vesa" if you have to.

*edit:*  This is what I mean:

1) Press ctrl+alt+f1 to drop down to a console.
2) Edit /etc/X11/xorg.conf with the text editor of your choice.  (I prefer vi or emacs, but try nano or pico for an easier experience)
3) Find the graphics card section
4) Change the "Driver" line to read:
```
Driver  "vesa"
```

Replace vesa with the driver of your choice, but it's a good starting point.

5) Run /etc/init.d/gdm start
6) Hopefully it works!

This modification won't be taking advantage of any special graphics hardware, so you'll still need to get the correct driver.  This is just a temporary solution.

---

### Post by I'm_pissed on 2007-03-07
Ok, I'll try that

---

### Post by I'm_pissed on 2007-03-07
vesa vga does not work with my video card

---

### Post by bryan.taylor on 2007-03-07
I'm not sure what ubuntu has as far as ati drivers.  I buy nvidia cards, but maybe there's someone else here with an ati card that knows what to do?

---

### Post by Jeproks on 2007-03-08
Hi guys, for this problem: It looks as though the drivers for your graphics card weren't loaded properly.  I'd like to help but you need to give a bit more hardware detail. :)  

But just so you know, the Xorg.conf initializes the gui system, it's kind of strange that your graphics card is not supported...but we'll get into that later if you give me more info to work with.  Are you even given prompt?

Build OS: linux 2.6.15.7 x86_64
Current OS: linux ubuntu 2.6.17-10-generic #2 SMP

(==) Log File: "/var/log/Xorg.0.log"
(==) Using config file: "/etc/X11/Xorg.conf"
(EE) No devices detected.

fatal server error
no screens found

As for the ATI problem, is it also your situation that this was a fresh install?  Regarding the standard drivers for ati on ubuntu, if I'm not mistaken, it's the mesa driver or the radeon (not the proprietary one).

---

