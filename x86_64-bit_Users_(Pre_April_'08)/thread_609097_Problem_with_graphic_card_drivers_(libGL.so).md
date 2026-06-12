---
title: "Problem with graphic card drivers (libGL.so)"
date: 2007-11-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Philipp717 on 2007-11-10
Hi there,

I have had this problem for a few days now, and I can't seem to find a solution, no matter what I try. A while ago, the new fglrx drivers appeared in the SID repos and after i upgraded to the newest version, my libGL.so.1 (and libGL.so.1.2) disappeared. Since then I was not able to restore those libs no matter what I tried. I even decided to remove the fglrx driver and go back to the open source ati driver, but when I try to install libgl1-mesa-glx i get the error "E: /var/cache/apt/archives/libgl1-mesa-glx_7.0.1-2_amd64.deb: unable to create `./usr/lib/libGL.so.1.2'"
Since i removed fglrx and haven't succeeded in installing the mesa driver, half my xorg has broken dependencies right now and I can't apt-get anything without deleting my whole system

I would really appreciate any help. Thanks a lot in advance.

---

