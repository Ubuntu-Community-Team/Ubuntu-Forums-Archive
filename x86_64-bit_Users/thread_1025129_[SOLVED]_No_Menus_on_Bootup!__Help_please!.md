---
title: "[SOLVED] No Menus on Bootup!  Help please!"
date: 2008-12-29
forum: x86 64-bit Users
---

### Post by MickSulley on 2008-12-29
Hi,

I am running 64 bit 8.10, kernel 2.6.27-9.generic

Up yesterday everything was fine, today when I boot up it all seems OK, but I do not get the panels top and bottom with the menus, status etc.  I see the normal desktop with the few icons that I normally see, but nothing at all at top or bottom.

What can I do??  It boots fine from live CD

With no menu I cannot do anything!  Help please!

---

### Post by mikewhatever on 2008-12-29
Try alt+f2. If a little 'Run Application' window opens, type in gnome-panel to start the panels.

---

### Post by MickSulley on 2008-12-30
alt F2 does nothing.  Is there any other way to get to it?

It does look like apart from the panels it has booted up, if I click on a desktop icon for a video it opens and runs OK. I am very confused by this.

Mick

---

### Post by MickSulley on 2008-12-30
This is now fixed.  I posted to the Absolute Beginners forum as well (same title if anyone is looking) and that provided the fix.

---

### Post by mikewhatever on 2008-12-30
Cool, glad it worked. Try using the 'history' command to look through the commands you issued. One of them may have removed gnome-panel.

---

### Post by MickSulley on 2008-12-31
Found it!  I did a complete removal of Evolution and all associated bits to try to fix a problem, evolution-data-server-common removes gnome-panel amongst other things.

I feel much better now I know how it happened.

Thanks for your help

---

