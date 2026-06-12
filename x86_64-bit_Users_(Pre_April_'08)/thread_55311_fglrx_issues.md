---
title: "fglrx issues"
date: 2005-08-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by illynova on 2005-08-08
Hey all,

Running Ubuntu Hoary Hedgehog on an AMD64 platform with an x800 (PCI-E). Downloaded and installed the fglrx drivers from ATI's website. However, when I tried running fgl_glxgears or any other gl program, I get an error saying that it cannot locate libGL.so.1

Thoughts?

---

### Post by PeP on 2005-08-08
try
glxinfo 
and check if the second or third line loks like 
Direct Rendering YES
if it's no, well you have no 3D accel.

---

### Post by illynova on 2005-08-10
glxinfo doens't work. Again, I get:

> 
scott@inti:~$ glxinfo
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


Any ideas?

---

### Post by Flac on 2005-08-11
did your replace "ati" with "fglrx" in your /etc/X11/xorg.conf file?

---

### Post by DancingSun on 2005-08-11
Do a file search for "libGL.so.1" and see if it exists in the first place. If it doesn't, the installation might have screwed something up.

You might want to uninstall the ATI drivers, then reinstall or use the drivers in the repository (if it exists).

Also, if you haven't done this yet, try searching for guides on installing ATI drivers on Ubuntu.  This way you can make sure that you are following the right steps.  And perhaps somebody already has encountered your problem and solved it.

---

