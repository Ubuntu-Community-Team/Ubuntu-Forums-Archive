---
title: "Powerbook G4 freezes / locks up on sleep / suspend"
date: 2006-05-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by natchris on 2006-05-15
Hello,

I am running the Dapper Drake beta on both a dual PowerMac G4 and a Gigabit Ethernet Powerbook G4 Ti (550).  On the PowerMac, everything is working great.

The Powerbook is having power management issues.  After a period of inactivity, when it should dim the screen, the computer freezes.  The display dims a little bit, the cursor will still move around the screen, the clock still keeps time and downloads continue (or at least appear to, but very slowly) -- but I cannot activate any windows, type, click on buttons, etc.  It is also impossible to wake the computer back up.

The same thing happens if I close the lid -- the display dims slightly (but remains on) and the computer basically locks up.  If I touch the power button for sleep, it brings up the shutdown dialog and if I choose suspend, it dims the screen and locksup

If I activate sleep from the command line, it works fine (turns off the display, the power indicator pulses) and I can wake it up by touching a button. 

I clearly need to reconfigure something, but I am not sure what.  Is it the Gnome power manager that I need to reconfigure or disable?

Nathan

---

### Post by ssam on 2006-05-15
do you have any odd hardware plugged in?

---

### Post by natchris on 2006-05-15
The only hardware I have plugged in is an Airport card (no external drives, no USB.  The problem manifests itself whether or not I have Airport enabled.  

No strange software running either (I installed the GUI powerprefs to manage pbbuttonsd options, Thunderbrid and Inkscape and that's it).

---

