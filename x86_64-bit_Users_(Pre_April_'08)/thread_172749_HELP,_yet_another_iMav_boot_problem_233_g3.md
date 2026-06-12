---
title: "HELP, yet another iMav boot problem 233 g3"
date: 2006-05-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by cosine7 on 2006-05-09
Hi,
I need help, i have just installed 5.10 on my system. install went fine, boots fine to the login, once i enter my login the system plays a little tune, but all i get is a biege screen and a pointer,  i have tried this by linear
[I]
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

If you restart Gnome and everything is in extreme slo-mo, you'll also need to edit xorg.conf to disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").[/I]

But to no evail, Suggestuions?

---

### Post by linear on 2006-05-09
The other thing to check for is the [date bug]("https://wiki.ubuntu.com/UbuntuDateBug").

---

### Post by cosine7 on 2006-05-09
Thanks linear, the date was set at 1900 :mrgreen: :mrgreen: :mrgreen:

---

