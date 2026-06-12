---
title: "[SOLVED] ubuntu only successfully boots up 1 out of 4 tries"
date: 2008-05-06
forum: x86 64-bit Users
---

### Post by Charles Vairin on 2008-05-06
Three out of time the progress indicator swings from side to side and bgings up Buzybox and starts printing stuff. Tried to reinstall but can't get through the partition section before the install crashes.  Any suggestions.

---

### Post by ASULutzy on 2008-05-06
Push alt+f1 at the busybox prompt and see what happens.

Alternatively, when you select what you want to boot from the grub entry, remove quiet and splash from the line and read what's going on during boot and why it fails.

---

### Post by Charles Vairin on 2008-05-06
Well it said
validation error fail error=-5
failed to ST Format(ero 0x40

---

### Post by Jouke74 on 2008-05-07
Are you sure your hardware is still ok? Namely the memory, IDE controller and harddisk?

---

### Post by Chayak on 2008-05-07
Sounds likes you've got some bad hardware.

---

### Post by Charles Vairin on 2008-05-07
The system is dual booted and starts up windows every time. When it does boot everything works.

---

### Post by ASULutzy on 2008-05-07
Still sounds like bad hardware to me... Have you checked the harddisk for errors?

---

### Post by Charles Vairin on 2008-05-10
Since this is a new system and I got the 7200 rpm disk could I need new drivers for the segate sata disk.

---

### Post by Charles Vairin on 2008-05-18
Well, I finally got the safe mode to boot all of the way and found that there is an option to boot normally or to repair boot packages.  So I repaired the packages and now everything is wonderful.  So much for bad hardware.  You gotta like punishment to do this!  Done

---

