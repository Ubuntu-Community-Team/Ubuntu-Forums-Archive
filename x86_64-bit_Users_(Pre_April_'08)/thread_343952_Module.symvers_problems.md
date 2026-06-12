---
title: "Module.symvers problems"
date: 2007-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by CanadianMan on 2007-01-22
I'm trying to get LIRC running on 64 bit dapper and i'm getting this warning:

WARNING: Symbol version dump /usr/src/linux-source-2.6.15/Module.symvers is missing; modules will have no dependencies and modversions.

which i'm told is leading me to this error:

[ 49.249823] lirc_mceusb2: no version for "lirc_unregister_plugin" found: kernel tainted.

does anyone have a solution for fixing this?  Heres a link to a previous post for reference.

[http://www.ubuntuforums.org/showthread.php?t=336141](http://www.ubuntuforums.org/showthread.php?t=336141)

Thanks.

---

### Post by hal10000 on 2007-01-22
Why are you running an old kernel, is this an older System?
Maybe updating to a recent kernel can fix it or you might have to compile your own kernel.

---

### Post by CanadianMan on 2007-01-22
I didn't realize I was running an outdated kernel.  I'll look up how to update it and write back in if the problem doesn't go away.

Thanks.

Edited: Is 2.6.15-27 not the latest version?  I'm using Dapper 64 bit.

---

### Post by CanadianMan on 2007-01-22
Well i've installed a fresh copy of Edgy on my computer.  This would have the latest kernel version correct since Edgy just came out not to long ago.  I still have the same problem.  Does anyone know how i get Module.symvers installed or what not?

Thanks.

---

### Post by hal10000 on 2007-01-25
Why do you want to compile the lirc source code?
Where did you get it from? (as a deb package from your ubuntu system or did you get it as a tar.gz or tar.bz2 file from somewhere out on the internet)

If you activate the "[COLOR="Red"]universe[/COLOR]" and "[COLOR="Red"]multiverse[/COLOR]" sections with your package manager (or manually in /etc/apt/sources.list) then you may install lirc AND lirc-x directly with your package manager (or with [COLOR="Red"]sudo apt-get update [/COLOR] AND [COLOR="Red"]sudo apt-get install lirc lirc-x [/COLOR] on a terminal).

I guess your problems are caused by using a version of the lirc source code which is incompatible with your kernel. In most cases it should not be necessary to install and/or compile the source code at all, so first try to install the lirc and lirc-x packages and only if this is not working install the lirc-modules-source package (using [COLOR="Red"]sudo apt-get install lirc-modules-source[/COLOR] )

EDIT: I just read this posting: [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy) and realized that you need the lirc-modules-source package.

---

