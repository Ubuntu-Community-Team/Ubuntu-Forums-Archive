---
title: "live cd help"
date: 2006-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Second_Player on 2006-03-10
whenever i use the live cd i get no video, si can hear the startup music but that it, its all black otherwise, and when i use video=ofonly it says there is something wrong with xwindows and i will get no gui.  i'm using a g3 i think, i just got it yesterday from my moms boss and i have no clue what i'm doing with macs.  if you decide to help than thankyou very much.

---

### Post by linear on 2006-03-10
You have problems with xorg.conf settings. The fix, after you get to that black screen, is to drop to a shell prompt and edit xorg.conf.
 
If you don't know how to do this:
 
After booting is complete,
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. make your edits (see below)
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo /etc/init.d/gdm restart (return) to restart Gnome
 
Check the settings for "HorizSync" and "VertRefresh". If you could specify the Mac model someone might be able to suggest proper values.

---

### Post by jdp on 2006-03-10
Could you be a little more specific on what machine you are using?  A G3 could refer to an iMac G3, a Beige G3, a B&W G3, an iBook G3, a PowerBook G3... ;)

---

