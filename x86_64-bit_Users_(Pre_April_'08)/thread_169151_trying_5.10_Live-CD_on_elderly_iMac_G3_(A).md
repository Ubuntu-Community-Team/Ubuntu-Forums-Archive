---
title: "trying 5.10 Live-CD on elderly iMac G3 (A)"
date: 2006-05-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Theo-Ubu on 2006-05-02
I'm working with an iMac 233Mhz, 100Mb (aprox.), 4Gb hard drive.   The machine will boot to the CD just fine when I hold down the "C" key.  It even gets 98% of the way through loading up.  It gets past the "Ubuntu" logo with the progress bar, but then when it switches back to text, then acts likes it's going to start up a desktop environment, it seems to hang forever.  The screen goes blank, then the CD drive just chatters away and I can never see anything happen.  Eventually I get tired of the chatter after more than three hours and I'll shut it down.

Is the machine to limited to run it, or are there some other avenues or tricks I can try?

Thanks!

---

### Post by chriscando on 2006-05-02
Im not familiar with Macs but I have had a simular problem when the resolution is incorrectly detected, everything is working in the background but you cant see it. Maybe try looking for some options at the bootup screen so you can set the resolution or change the video driver. What worked for me was adding something like 'xdrvr=vesa'

---

### Post by linear on 2006-05-02
My standard response for iMac G3's follows, though I don't know if yours has the same video card as some of the others.
 
The fix, after you get to that black screen, is to drop to a shell prompt and edit xorg.conf.
 
If you don't know how to do this:
 
After booting is complete,
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. make your edits (see below)
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo /etc/init.d/gdm restart (return) to restart Gnome
 
At the very least you'll need to modify "HorizSync" to 60-60 and "VertRefresh" to 75-117. Both are in the monitors section.
 
If you restart Gnome and everything is in extreme slo-mo, you'll also need to edit xorg.conf to disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").

---

