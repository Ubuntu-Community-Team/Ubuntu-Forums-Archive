---
title: "Can't install Nessus 3"
date: 2006-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by neptune on 2006-04-20
Hey everyone, I'm a fairly new Linux / Ubuntu user (at least on AMD64 arch).

I tried to install Nessus 3 using this thread [http://ubuntuforums.org/showthread.php?t=134520](http://ubuntuforums.org/showthread.php?t=134520) but during install, I get the following error:
> dpkg: error processing Nessus-3.0.2-debian3_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 Nessus-3.0.2-debian3_i386.deb


Can someone please assist?

Thanks.

---

### Post by Thirsteh on 2006-04-20
You're trying to install the Nessus package for the i386 architecture, where you'd want to install one for amd64.

You need to download the amd64 package instead, if it exists, and sudo dpkg -i that package instead of the i386 version.

---

### Post by neptune on 2006-04-20
Yes, I figured as much. 

There isn't an am64 package available from [www.nessus.org](www.nessus.org) for version 3.x unfortunately.

Does this mean I'm out of luck?

---

