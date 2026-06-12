---
title: "Help with wine"
date: 2006-08-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Complitric on 2006-08-08
I can not get wine installing, and I am not sure what is wrong.  I have added the Universe repositories, and done apt-get update.  However, when I give the command apt-get install wine, it gives me:

sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate


I am running Ubuntu +K 64 bit.

---

### Post by Jagot on 2006-08-08
WINE is in the universe repository which you need to enable first.  See either of these links:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

However, the version of WINE in the repos is only for i386.  This seems to be the best way for 64bit at the moment:

[http://www.ubuntuforums.org/showthread.php?t=185557](http://www.ubuntuforums.org/showthread.php?t=185557)

---

