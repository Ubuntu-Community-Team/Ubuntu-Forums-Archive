---
title: "help finding the lib32ncurses5 package for 8.10"
date: 2009-04-22
forum: x86 64-bit Users
---

### Post by robert3353 on 2009-04-22
Hello,
I just installed the Linux version of Prey and it will not run.  After looking at the Prey for Linux website at [http://icculus.org/prey/](http://icculus.org/prey/) I discovered that there are issues with Ubuntu AMD64 distros.  

It seems from looking at the bug report that has been filed [https://bugs.launchpad.net/ubuntu/+bug/199952](https://bugs.launchpad.net/ubuntu/+bug/199952)

"There is a lib32ncurses5 package to supply x86 compatibility libraries to amd64 distros, but there is no lib32ncursesw5 package. This means 32-bit ncurses apps running on an amd64 box can't use Unicode (and those that would try to simply would refuse to start at all, due to a missing dependency).

This is normally provided by the libncursesw5 package in a x86 Ubuntu install.

The missing files/symlinks, specifically, would be:

    /lib32/libncursesw.so.5.6
    /lib32/libncursesw.so.5
    /usr/lib32/libncursesw.so

--ryan."

I am running Ubuntu 8.10 amd64 distro and when looking for the required library  lib32ncurses5 in the package manager that it in fact does not exist, at least on this version of Ubuntu.  Does anyone know where I can find this package and how to get it installed on Ubuntu 8.10?  Is there a different repository I can add to my current list that would have this package available for install?

Thanks for any help you may be able to supply.
Robert

---

### Post by Cappy on 2009-04-23
You can install getlibs from here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
and run
```
sudo getlibs -p libncursesw5
```

---

