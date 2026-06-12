---
title: "file browser not working in apps"
date: 2009-04-16
forum: x86 64-bit Users
---

### Post by larrinh on 2009-04-16
I recently installed ubuntu 8.10 for about the 5th time (working out bugs with different versions) and have gotten everything working except for one thing that is quit bothersome. If I open a file browser from an app, say to add an attachment to Thunderbird or import music to Ryhtembox, the file browser is completely unresponsive. I can't do anything with it. Is there a way to reinstall the package that runs this.

---

### Post by Vadi on 2009-04-16
I believe *libgtk2.0-0* is reponsible for this. If reinstalling doesn't help though, let me know - this is a bug that would need fixing.

---

### Post by larrinh on 2009-04-16
I tried reinstalling libgtk2.0-0, libgtk2.0-cil, libgtk2.0-common and libgtk2.0-bin. Now there are no graphics at all in the file browser window. At least this is the right path, maybe the wrong direction, but the right path.

---

### Post by Vadi on 2009-04-16
Can you please provide a screenshot?

---

### Post by larrinh on 2009-04-17
After 2 restarts (working on a way to unmount cifs shares at shut down) the problem is back to the original symptoms. Just no reaction to the mouse or keyboard in the file browser windows. I can still click on the Cancel button or the X in the corner and it works but I can not navigate the window.

I should mention that the file browser works fine if I open it from the Applications menu and not from within a running app.

---

### Post by Vadi on 2009-04-17
Ah, you have something mounted... does it work fine without it being mounted?

---

### Post by larrinh on 2009-04-17
I unmounted all of the shares that I had mounted and the problem remains. I believe that the problem was there right from the start after install.

---

### Post by Vadi on 2009-04-17
I suspect it was a damaged CD then or somesuch - I haven't heard about this issue, and it does look paculiar.

If you installed from the CD, remember if you did the disk check?

---

