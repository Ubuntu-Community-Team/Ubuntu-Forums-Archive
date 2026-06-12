---
title: "x200 on msi rs480"
date: 2005-11-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by sv_nitc on 2005-11-24
Hi I Could install the 64 bit on msi rs480 board but i am still unable to start the xorg x server . So now i can use the text interface only. pls help

---

### Post by Ribs on 2005-11-24
Do you get any errors?

Check the contents of /var/log/Xorg.0.log (run "less /var/log/Xorg.0.log"). See the bottom of the file, that's usually where there is a tell-tale sign of a problem.

---

