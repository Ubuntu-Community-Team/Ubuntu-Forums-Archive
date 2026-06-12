---
title: "Crossover-7.0.sh error while installing"
date: 2009-05-11
forum: x86 64-bit Users
---

### Post by Tilex on 2009-05-11
Hi guys,

At home (Jaunty amd64 - fresh install), I installed Crossover 7.0.2 using the installer script and everything went smoothly.

However, on another computer (Jaunty amd64 - fresh install), I'm trying to install the same script and it gives an error :

```
./setup.sh: 201: /home/resyst/.setup8501: not found
The setup program seems to have failed on x86/glibc-2.9
Check the system requirements at:
http://www.codeweavers.com/products/cxoffice/requirements/

You might be missing the 32bit compatibility libraries

```

There seems to be a compatibility issue with the 64bit?  Would you guys happen to know what went wrong ?  I tried re-installing glibc2.9 (which is part of libc) and it didn't help.

Thanks !

---

### Post by pixel :-) on 2009-05-11
Untill you solve it, try surviving on wine

1.20 Wine installs flawlessly as a .deb package, so i'm surprised that the commercial version doesn't offer at least that. You should be able to find a package for your system easily, with all dependencies taken care of automatically.

are you trying to install the 32bit package in a 64 bit system?
maybe ia32-libs will solve the problem, but you may want to install the actual 64 bit version. You actually reinstalled the 64 bit version of the library, the 32 bit version is contained in the above package. Find the 64 bit programme.

If its something more obscure you should give more info.

---

