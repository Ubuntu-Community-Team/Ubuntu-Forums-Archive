---
title: "Trying To Run Live CD On Indigo iMac"
date: 2005-12-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lady Sheba on 2005-12-13
I just got the Live CD and I want to run it on my indigo 400Mhz iMac. When I go into the Startup Disk control panel, I can't choose the CD--grayed out. Am I missing something, or will I have to do a formal install (which scares me, because that would wipe my hard drive)? :confused:

---

### Post by linear on 2005-12-13
With the CD in the drive, restart and hold down the "c" key until the LiveCD boots. If Mac OS starts instead, then any of the following could be the problem:

1. Bad CD. Try re-burning at a slow speed (4x).
2. Your Mac won't boot from a CD.
3. There's a problem with the CD drive.

---

### Post by Lady Sheba on 2005-12-14
I did that. The computer looked like it was booting up just fine, but after the little music warble, the screen was black for a loooooooooog time. I've got no patience, so I shut everything down and went to bed. :razz: 

I'm going to install it instead, but I have to backup the important stuff on my external hard drive. Now I'm wondering...can I put OS9 on the external drive and let Ubuntu have the internal drive?

---

### Post by linear on 2005-12-14
If you mean you saw all the text Ubuntu startup messages, then I think you have the same problems with xorg.conf settings that afflict many others. The fix, after you get to that black screen, is to drop to a shell prompt and edit xorg.conf.

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

