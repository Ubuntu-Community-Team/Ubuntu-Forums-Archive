---
title: "Problem with X"
date: 2005-08-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by zarathustra on 2005-08-17
Something hasn't installed right. When I run fglrxinfo I get:

> nick@kitsune:/lib/modules/fglrx$ fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


I get similar errors when attempting to compile anything graphical.

---

### Post by invalid on 2005-08-18
Try this

> 1. Stop gdm. From the text based terminal do the following.
2. sudo modprobe -r fglrx.
3. sudo apt-get remove fglrx-6-8-0.
4. sudo /bin/rm -R /lib/modules/fglrx.
5. sudo apt-get install xlibmesa-gl (this was giving me problems when trying to update from within synatic). Now it runs fine and updates the system.
6. locate the fglrx-6-8-0_8.10.19-2_i386.deb (this was created with alien using the RPM package from ATI).
7. sudo dpkg -i --force-overwrite <PATH>/fglrx-6-8-0_8.10.19-2_i386.deb. This will install necessary libraries and create the module source under /lib/modules/fglrx.
8. change to /lib/modules/fglrx/build_mod.
9. sudo sh make.sh. Change to /lib/modules/fglrx.
10. sudo sh make_install.sh.
11. modprobe fglrx.
12. Restart gdm.

from here:
[http://ubuntuforums.org/showthread.php?t=22655&highlight=loading+shared+libraries%3A+libGL.so.1](http://ubuntuforums.org/showthread.php?t=22655&highlight=loading+shared+libraries%3A+libGL.so.1)

Cheers,
Cb

---

### Post by zarathustra on 2005-08-21
Thanks, followed that. I had a problem building the module in the last step received the error:

> Error inserting fglrx /lib/modules/2.6.10--5-amd64-generic/kernel/drivers/video/fglrx.ko no such device

However, GDM started up again and fglrxinfo seems to work...

---

