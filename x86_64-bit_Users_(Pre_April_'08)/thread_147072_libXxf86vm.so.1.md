---
title: "libXxf86vm.so.1"
date: 2006-03-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hoffmann on 2006-03-19
Hello:

I realized that in both /usr/lib and /usr/lib64 directories I have the libXxf86vm.so.1.0.0 file. Moreover, I have:

libXxf86vm.so.1 -> libXxf86vm.so.1.0.0

However, when I try to run some programs, I get the following error message:

"error while loading shared libraries: libXxf86vm.so.1: cannot open shared object file: No such file or directory"

Could anyone, please, help me to solve this problem? :cry: 

Thanks!
Hoffmann

---

### Post by boddha on 2006-03-19
just out of curiousity are you trying to use a 32 bit package in the AMD64 distro? if not I would recommend  to reinstall the package. An easy way is to search for the package libxxf86vm1 in synaptic then right click it and choose "mark for reinstallation". then click the  "apply" button. If you have installed a 32bit package in an AMD64 distro you will have to manually download the libxxf86vm1 package from an unbuntu mirror, extract the file you need and copy it the /lib32 directory.  There are better instructions elsewhere on this forum.

---

### Post by Hoffmann on 2006-03-19
I have installed a 32-bit package in my AMD64 distro.

How can I manually download the libxxf86vm1 package from an unbuntu mirror, since there I have just isoimages? :( 

Hoffmann

---

### Post by Hoffmann on 2006-03-20
Hello boddha,

I just realized how to manually download packages from Unbuntu mirrors. I already installed the (32-bits) libraries I needed, and all is working fine.

Thanks!

Best,
Hoffmann

---

