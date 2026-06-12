---
title: "I/O SATA Bench Marks Tools"
date: 2007-01-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Didjit on 2007-01-13
Looking for an application to measure speed of my SATA drive. Seems slow to me. Any suggestions?

Didjit

---

### Post by cylon359 on 2007-01-14
You could do a simple sudo hdparm -tT /dev/sda (or whatever device).  If you want better statistics, look at the bonnie++ package.

---

