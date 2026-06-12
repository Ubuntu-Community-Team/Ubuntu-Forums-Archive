---
title: "how to give wine more ram?"
date: 2007-11-07
forum: Wine
---

### Post by fourthdimension on 2007-11-07
Hey All

I'm using wine to emulate 3 windows programs at once:  digital paint (paintball2) - the linux version isn't ported well -, the paintball2 server browser, and ventrilo (required by my clan).  When I do that, ventrilo cuts out when it is not in the foreground.  I don't think it's getting enough ram.  Is there a way to give wine more ram, like I would with a windows task manager?
Thanks.

---

### Post by The Noble on 2007-11-08
To my knowledge, wine gets as much ram as it desires as long as it does not steal from the main desktop. You can only choke so much ram from the OS before everything slows to a crawl, so this would be a good time to get more RAM. Where I live, a gig is ~30 USD, a far cry from the 80 USD a year ago. You may want to try using a "-n 20" command after the execution of the code to give it priority, or alternatively running a lighter GUI (xfce4 instead of Gnome, etc) to free up some RAM. Also close Firefox or Azureus, as they each take quite a bit of memory.

---

### Post by cogadh on 2007-11-08
You can also try running the programs without your window manager running (Gnome, KDE, XFCE, whatever), which will free up a big chunk of RAM. Since Wine doesn't require the window manager to do what it does (it just needs the X server), leaving it running can get in the way. Click on the "Stuff I've learned about Wine" link in my sig and go to the "Advanced Stuff" section, it explains how to create a launch script that can do what you need. You may need to modify it some to accommodate the separate programs you are running, but it should work fine.

---

### Post by Ardrias on 2007-11-08
RAM has nothing to do with Ventrilo. The "problem" is that X handles the focusing differently that Windows does, or so I've heard. 

In short... you have to keep Ventrilo focused to talk (listening should still work, at least it does when using ALSA) or use ventriloctrl.

---

### Post by Ferrat on 2007-11-08
Wine uses as much RAM as it can but it only uses 64MB VRAM unless you change it in the regedit to the real value 

As for Vent, there is some issues getting it to run smoothly, when I was playing WoW and using vent I had to use the AOSS (/alsa - oss overlay pkg) and make sure I started vent before WoW and make sure my press to talk button wasn't assigned in WoW.

---

