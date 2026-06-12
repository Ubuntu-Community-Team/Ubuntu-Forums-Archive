---
title: "Linux-rt installed but no new entry in lilo?"
date: 2007-12-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dieter@be on 2007-12-13
Hi, I'm on gutsy gibbon using amd64

I have the default kernel, which works fine, but for audio recording i want a low-latency kernel so i installed linux-rt.

The problem is: i want to be able to choose between these two when booting.  Now it always just boots linux-rt without showing me a menu or anything.

The bootloader is lilo btw, i didn't chose this but ubuntu picked this for me when i decided to use lvm to put my system on.

Thanks
Dieter

---

### Post by crazee_canuck on 2007-12-31
I'm kinda late to responding but if you still have the problem could you paste your /etc/lilo.conf here?

---

