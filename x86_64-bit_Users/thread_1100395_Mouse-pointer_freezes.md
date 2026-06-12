---
title: "Mouse-pointer freezes"
date: 2009-03-19
forum: x86 64-bit Users
---

### Post by marcelkoopman on 2009-03-19
I'm having problems with Intrepid AMD64. Frequently the mouse pointer freezes and the system eventually locks up.

What could be the problem? I can still type but the mouse pointer is gone. What logs should I check? I have a logitech mouse GS, never had problems with it before.

---

### Post by lemming465 on 2009-03-22
If you are using proprietary ATI or Nvidia video drivers, try reverting to the open source ones.  Or upgrade to Ubuntu 9.04 Jaunty alpha 6 if you dare (sudo update-manager -d); that might be better (it's what I'm running on).

The first log files to try are /var/log/messages, /var/log/Xorg.0.log, and /var/log/daemon.log.

---

