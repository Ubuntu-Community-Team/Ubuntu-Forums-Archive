---
title: "How to load 64 bit deb files"
date: 2006-12-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by jlr4u on 2006-12-28
I have problems with a wireless network card and video drivers for NVIDIA.
From my research I loaded:

     nvidia-glx_1.0.8774+2.6.17.5-11_i386.deb

It would not allow me to load the 64 bit version

     nvidia-glx_1.0.8774+2.6.17.5-11_amd64.deb

My kernel is 2.6.17-10-generic.
My CPU is ADM Athlon 64-3500+Venice 2.2Ghz

What do I do to get the 64 bit deb files to load?

---

### Post by Gamezguy on 2006-12-28
What kernel type are you using? (i386, etc)

---

### Post by jlr4u on 2006-12-28
I believe I am running i386.   

Perhaps I need to stay away from the 64 bit.  I assumed I would have to re-build the kernel for what I wanted and wanted to see what others say.

---

### Post by pseudonym on 2006-12-28
> **jlr4u said:**
> I believe I am running i386.   

Perhaps I need to stay away from the 64 bit.  I assumed I would have to re-build the kernel for what I wanted and wanted to see what others say.
Yes, that 64-bit nvidia driver will only work if you're running a 64-bit ubuntu. If you want to make the jump to 64-bit you'll need to wipe your 32-bit install and download a 64-bit iso and install that. I don't think it's possible to upgrade via synaptic or apt-get.

---

