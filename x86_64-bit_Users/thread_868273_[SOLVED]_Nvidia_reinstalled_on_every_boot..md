---
title: "[SOLVED] Nvidia reinstalled on every boot."
date: 2008-07-23
forum: x86 64-bit Users
---

### Post by PinkFloyd102489 on 2008-07-23
I have Ubuntu 8.04 on my Dell Inspiron 1720 laptop, with a GeForce 8600M GT in it. I usually like cutting edge, so I downloaded the x86_64 driver from Nvidia's website and installed it. Install went smooth, just like on my 32bit systems.

Only problem is, I have to reinstall upon every boot in order to normalize my graphics. If not, X tries to start but then fails and goes into low-graphics mode. After reinstalling the drivers, everything is fine.

Is anyone else having this problem or know what to do?

---

### Post by Neo0351 on 2008-07-23
try this
```
gedit /etc/default/linux-restricted-modules-common
```
and make the last line look like this
```
DISABLED_MODULES="nv"
```

---

### Post by PinkFloyd102489 on 2008-07-23
Thanks, that worked!

---

### Post by NullHead on 2008-07-23
I usually purge nvidia-kernel-common to have my nvidia driver install and stay that way. I guess that works too. I've never heard of doing it that way, but as long as it works, I guess you'll be happy. :popcorn:

---

