---
title: "ia32-libs won't install"
date: 2008-05-09
forum: x86 64-bit Users
---

### Post by Creshal on 2008-05-09
Evening,
Whenever trying to install the ia32-libs, dpkg aborts with an error: > Cannot create »./usr/lib32/libGL.so.1.2«: No such file or directory (sth. like this, got the german version). I already searched teh forum and tried all solutions I could find. Nope, it's not related with a specific driver, got the problem with both fglrx and nvidia (and yes, I'm using a respective card fitting for that driver). Nope, correcting the symlink didn't work. Nope, reinstalling the driver(s) didn't work. Nope, all dependencies are installed, and yes, they have the correct version (if the information of the ia32-libs-package is correct...) And nope, I'm pretty sure that I'm using a 64 Bit CPU and OS.

Any other ideas?

---

### Post by Kilz on 2008-05-09
> **Creshal said:**
> Evening,
Whenever trying to install the ia32-libs, dpkg aborts with an error:  (sth. like this, got the german version). I already searched teh forum and tried all solutions I could find. Nope, it's not related with a specific driver, got the problem with both fglrx and nvidia (and yes, I'm using a respective card fitting for that driver). Nope, correcting the symlink didn't work. Nope, reinstalling the driver(s) didn't work. Nope, all dependencies are installed, and yes, they have the correct version (if the information of the ia32-libs-package is correct...) And nope, I'm pretty sure that I'm using a 64 Bit CPU and OS.

Any other ideas?

Its saying that the directory doesnt exist. What is the results of ```
uname -a
``` when typed in the terminal?

---

### Post by gsmanners on 2008-05-09
I think the procedure for the workaround is:

1) Remove video drivers
2) Update ia32-libs
3) Reinstall video drivers

If that fails, try:

dpkg -S libGL.so.1.2

and remove the packages indicated. Then reinstall ia32-libs.

---

