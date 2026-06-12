---
title: "How do I reassign eth0?"
date: 2007-08-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by TheAbyssDragon on 2007-08-25
After some issues with 64bit 7.04 not running due to xserver problems, I got a 64bit version of 6.06 up. However, when I check iwconfig and ifconfig, both my ethernet and wireless are assigned to eth0. How can I reassign my wireless to eth1?

---

### Post by stmiller on 2007-08-25
I think you can edit the file

/etc/iftab

to change this.

---

