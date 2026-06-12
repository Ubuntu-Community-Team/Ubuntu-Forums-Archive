---
title: "64-bit ubuntu installed on 32-bit PC"
date: 2008-09-04
forum: x86 64-bit Users
---

### Post by Bulletbeast on 2008-09-04
Yesterday, I installed Hardy on a mate's PC using the "Install within Windows" option. However, I forgot that my Ubuntu CD is 64-bit -- which said mate's PC is not. Is there now a way to convert his installation into a standard i386 one without reinstalling?

---

### Post by soxs on 2008-09-04
I don't think so, and if it would work, you will still have 100dreds of MiBs wasted for unuseable 64 bit .debs, libraries and other files which you will never be able to remove properly without _hours_ of searching.

I suggest you, wether it is possible to convert to 32 bit or not, reinstall it.

---

### Post by insane_alien on 2008-09-04
not really, you would have to change far too many files and manually at that as you can't boot it up.

just delete it and use an i386 disk.

---

### Post by bford16 on 2008-09-04
> **Bulletbeast said:**
> Yesterday, I installed Hardy on a mate's PC using the "Install within Windows" option. However, I forgot that my Ubuntu CD is 64-bit -- which said mate's PC is not. Is there now a way to convert his installation into a standard i386 one without reinstalling?
What kind of PC is it?  You should not have been able to install 64-bit Ubuntu on a 32-bit PC in the first place.

---

### Post by philinux on 2008-09-04
> **bford16 said:**
> What kind of PC is it?  You should not have been able to install 64-bit Ubuntu on a 32-bit PC in the first place.


Obviously wubi dont care :lolflag:

---

### Post by Thelasko on 2008-09-04
> **philinux said:**
> Obviously wubi dont care :lolflag:

Sounds like a bug to me.

---

### Post by Thelasko on 2008-09-04
It sounds similar to trying to "upgrade" to 64-bit, only in reverse.  [That doesn't work]("http://ubuntuforums.org/showthread.php?t=366707"), so this won't work either.

---

### Post by Gabt on 2008-09-04
If its installed, then your CPU must be 64bit. Use it and enjoy.

---

### Post by soxs on 2008-09-04
> **Gabt said:**
> If its installed, then your CPU must be 64bit. Use it and enjoy.

As it seems , it's obviously not _that_ simple... go and file a bugreport for wubi.. or never use wubi, just boot the alternate iso ;-)

---

### Post by Sef on 2008-09-04
Applications > Accessories > Terminal

paste or type this code in it:

> uname -a

It will tell you if the computer is 23 or 64-bit hardware.

Mine (64-bit) says this:

>  2.6.27-2-generic #1 SMP Thu Aug 28 17:18:43 UTC 2008 x86_64 GNU/Linux


It will have i686 (or something similar), if it is 32-bit.

---

