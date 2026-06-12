---
title: "Wine compile returns &quot;No OpenGL library found on this system&quot;"
date: 2011-09-28
forum: Wine
---

### Post by travlemon on 2011-09-28
Hello,

I am trying to compile Wine from source, and it absolutely refuses to compile for me.  As mentioned in the thread title, I am receiving the following error when I run ./configure:

```
configure: WARNING: No OpenGL library found on this system.
OpenGL and Direct3D won't be supported.
```

I've been installing different dev packages for a while now, anything that has to do with OpenGL.  The suggestions I found through Google searching mentioned that the package **libgl1-mesa-dev **and related packages should be what I need, however I installed a whole bunch and I still receive the error.

Does anyone know what other OpenGL packages this thing could possibly want?

Thanks in advance!

---

### Post by Perfect Storm on 2011-09-28
Moved to Wine Section.

---

### Post by travlemon on 2011-09-28
> **Artificial Intelligence said:**
> Moved to Wine Section.

Thank you! I did not realize there was a Wine section, my apologies!

---

### Post by travlemon on 2011-09-29
I finally found my solution to this problem...It turns out that I had all of the correct packages installed, but it wasn't compiling for some reason.

**Solution: **For other reasons, I install libgl1-mesa-swx11 and libgl1-mesa-swx11-dev, which forced the uninstall of some other mesa packages that were already on the system.  I tried to ./configure again, and got the same error.  This time,  I re-ran **sudo apt-get build-dep wine** and it reinstalled the packages that libgl1-mesa-swx11 uninstalled.  

I ran ./configure again, and it configured without error.  For whatever reason, I guess the package just needed to be reinstalled.  In any case, all is well!

---

