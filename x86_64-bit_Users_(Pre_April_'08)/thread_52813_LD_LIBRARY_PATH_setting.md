---
title: "LD_LIBRARY_PATH setting"
date: 2005-07-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by bukagedi on 2005-07-29
I had to set up LD_LIBRARY_PATH after MONO installation and was surprised: something cleans up /usr/local/lib setting in LD_LIBRARY_PATH:
   I set it in /etc/ld.so.conf and launched ldconfig - loader finds no 
   additional libraries,
   on second step I created new file in /etc/X11/Xsession.d and wrote my 
   settings there;  LD_LIBRARY_PATH was wiped again; my file was
   executed - all settings except LD_LIBRARY_PATH are visible,
   system began to work after I wrote  LD_LIBRARY_PATH at start of
   ~/.bashrc.
Can anybody tell me where and when UBUNTU wipes /usr/local/lib setting from LD_LIBRARY_PATH and how can I to perform system wide setting of this variable: I don't like to repeat the same settings for every user.

Gediminas Bukauskas
[email]audriusb@homelan.lt[/email]

---

### Post by joshuapurcell on 2005-07-29
> **bukagedi]I had to set up LD_LIBRARY_PATH after MONO installation and was surprised: something cleans up /usr/local/lib setting in LD_LIBRARY_PATH:
   I set it in /etc/ld.so.conf and launched ldconfig - loader finds no 
   additional libraries,
   on second step I created new file in /etc/X11/Xsession.d and wrote my 
   settings there said:**
> audriusb@homelan.lt[/email]
Try putting it in /etc/bash.bashrc. If you put it there is should be accessible from everywhere.

---

