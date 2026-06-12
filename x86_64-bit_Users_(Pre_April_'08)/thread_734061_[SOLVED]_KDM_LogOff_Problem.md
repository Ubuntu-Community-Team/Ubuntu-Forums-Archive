---
title: "[SOLVED] KDM LogOff Problem"
date: 2008-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by prince_niceguy on 2008-03-24
I am having this strange problem with kdm. I can login into KDE and everything works fine. But when I log off, there just a blank black screen, the login screen does not come up again. Anyone else having the same issue? Can some one guide me in which logs to check to debug. I have checked Xorg.log and kdm.log but there are no errors.

---

### Post by dokdoom on 2008-03-25
That's weird nothing is showing up in those logs. To make sure, replicate the error by logging off. From your terminal run:

ls -ltr /var/log

This will show you the logs which have been changed according to time. Tail all of the logs that match up to the timestamp. If you aren't finding anything then:

cat /var/log/<log>.log |grep EE

and then grep for WW

Let me know if you find anything.

---

### Post by prince_niceguy on 2008-03-25
am currently hooked on to gdm and using kde on top of that. will try out your suggestion once have some time. right now busy with work as going for extended vacation... :D

---

### Post by prince_niceguy on 2008-03-26
seems recent updates have fixed the issue. now it is working fine.

---

