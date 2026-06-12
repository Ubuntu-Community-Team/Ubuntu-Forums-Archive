---
title: "change time zone in chroot"
date: 2005-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by BoyOfDestiny on 2005-11-20
I noticed the clock option in zsnes (through chroot) is about 3 hours off... How exactly do I just change the time zone in a chroot? 

dchroot -d
dpkg-reconfigure ?????

Thanks!

---

### Post by BoyOfDestiny on 2005-11-21
Nevermind. For those curious.

dchroot -d
sudo tzconfig

Voila!

---

