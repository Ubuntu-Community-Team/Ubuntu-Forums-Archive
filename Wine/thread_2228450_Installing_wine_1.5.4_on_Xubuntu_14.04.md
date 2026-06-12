---
title: "Installing wine 1.5.4 on Xubuntu 14.04"
date: 2014-06-07
forum: Wine
---

### Post by theangryspider2k on 2014-06-07
I was directed here from the winehq forums for help with binary packages. I got a .deb file from the [http://wine.budgetdedicated.com/archive/](http://wine.budgetdedicated.com/archive/) binary archive (which now just goes to a blank page for me. Any ideas why that is?) and tried to install it but it doesn't install because of dependency problems. This is the output from "sudo dpkg -i wine1.5-dbg_1.5.4-0ubuntu1~ppa1~precise1+pulse17_i386.deb":
```
Selecting previously unselected package wine1.5-dbg:i386.
(Reading database ... 344775 files and directories currently installed.)
Preparing to unpack wine1.5-dbg_1.5.4-0ubuntu1~ppa1~precise1+pulse17_i386.deb ...
Unpacking wine1.5-dbg:i386 (1.5.4-0ubuntu1~ppa1~precise1+pulse17) ...
dpkg: dependency problems prevent configuration of wine1.5-dbg:i386:
 wine1.5-dbg:i386 depends on wine1.5-i386 (= 1.5.4-0ubuntu1~ppa1~precise1+pulse17); however:
  Package wine1.5-i386 is not installed.

dpkg: error processing package wine1.5-dbg:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine1.5-dbg:i386
```
Shouldn't this deb be installing wine1.5-i386? Am I doing something wrong?

My PC specs:
Intel i3 2100
EVGA GT630 2GB - driver version 331.67
4GB RAM
Xubuntu 14.04

---

### Post by Toz on 2014-06-07
Hello and welcome to the forums.

As opposed to installing a package from a previous ubuntu version (which can be problematic because of dependency issue like the one you've run into), you might want to consider using [PlayOnLinux]("http://www.playonlinux.com/en/") (look for it in the repositories). PlayOnLinux is a front-end to wine and one of its many features is that it allows you to run multiple versions of wine, including the version you are interested in - all seamlessly integrated into the application (no extra packages for you to manually download). From within the application, go to Tools->Manage Wine Versions to install the wine version you are interested in.

---

### Post by adec2 on 2014-06-07
I concur with Toz above. Using Playonlinux makes it much easier to swap between wine versions within containers. I use it all the time

---

### Post by theangryspider2k on 2014-06-08
PlayOnLinux is working nicely. Thanks!

---

