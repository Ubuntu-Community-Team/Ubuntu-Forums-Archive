---
title: "Booting Ubuntu Studio in Safe Mode"
date: 2008-09-14
forum: x86 64-bit Users
---

### Post by afrodeity on 2008-09-14
I've tried booting Ubuntu Studio in restore mode, dropped down to shell, and used dpkg to edit xorg but all I get is a series of menus about my keyboard, nothing about the video. How do I get the video into safemode, like Hardy?

---

### Post by Thelasko on 2008-09-15
dpkg-reconfigure no longer configures X video.  When you are in the terminal enter "xfix" (you may need sudo) and see what that does.

Were you ever able to bring up X in UbuntuStudio?  If not, try my install method in my sig.

---

