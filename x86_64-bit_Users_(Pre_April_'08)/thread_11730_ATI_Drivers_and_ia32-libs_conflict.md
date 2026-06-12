---
title: "ATI Drivers and ia32-libs conflict"
date: 2005-01-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by froust on 2005-01-18
I was trying to update the fglrx drivers, and got this error message:

(Reading database ... 70552 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu1_amd64.deb (--unpack):
trying to overwrite `/usr/lib32/libGL.so.1', which is also in package ia32-libsErrors were encountered while processing:
/var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas?

---

### Post by daniels on 2005-01-18
Known issue, I've got a fix locally, will upload soon.

---

### Post by froust on 2005-01-20
awesome... thanks :D


*waits patiently for 3d*

---

### Post by daniels on 2005-01-20
I think this went in yesterday or so.

---

### Post by froust on 2005-01-21
It was, and they installed beautifully... Thanks!



unfortunately, my resolution is stuck at 640x480... fglrxinfo shows a radeon 9500 being installed (i have a 9700 pro) and glrxgears gives 2000fps... Any thoughts?

---

