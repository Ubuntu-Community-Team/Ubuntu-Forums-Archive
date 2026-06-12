---
title: "Root Privilages"
date: 2006-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by confusimo on 2006-10-27
I got a new printer.  Samsung ML-2510-XAA.  I downloaded the linux driver from their website.  I don't want to use a terminal.  I want to use the gui.  But all the files are locked.  And if I click on any of them they say I need Root Privilages.  How do I enable Root Privilages.  I don't need permanent Root Privilages.  Just for the install.  How do I get Root Privilages.

Ubuntu DD 64-bit 6.06.

Thanks,
Confusimo

---

### Post by Sarisar on 2006-10-27
press alt+f2 to bring up a 'run application' box.  Type in:
gksudo nautilus

It will ask for your password then give you nautilus with full root privs.  Just remember you can seriously screw your PC up if you muck up the wrong file :)

---

### Post by confusimo on 2006-10-27
That was it thanks.  Nice temporary fix.

Confusimo

---

### Post by Sarisar on 2006-10-28
No probs - I used to use it all the time until I added the scripts to do it (root gedit - from automatix I think).  Now if there is a file I can edit I can right-click and edit it (after entering password anyway).

---

