---
title: "Application Question"
date: 2005-07-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by sunmicroman on 2005-07-08
This may be kind of a stupid question but I am going to ask anyway since I have no experience yet on 64 bit Linux systems. I was curious to know if all 32 bit Linux applications will run on a 64 bit Linux OS. Will they just run in "32 bit mode" such as on a 64 bit Windows or Mac boxen? Or do I need to recompile all the apps to work on a 64 bit system?

---

### Post by NickB on 2005-07-08
Some 32-bit applications can run in 32-bit mode using the libraries in the lib32 directories, but these are few.  Statically linked 32-bit binaries work fine.  However, for most 32-bit applications you need a chroot'ed environment (see [http://www.ubuntuforums.org/showthread.php?t=24575](http://www.ubuntuforums.org/showthread.php?t=24575)).

I had no problem setting this up, but I'm fairly experienced with debian.  YMMV.

Nick

---

