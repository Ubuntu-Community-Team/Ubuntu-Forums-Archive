---
title: "blackdown 1.4.2rc1 + eclipse 3.0.1 no go :("
date: 2005-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by yatesco on 2005-02-25
All,

I have been running blackdown 1.4.2rc1 J2SDK and eclipse 3.0.1 (both for AMD64) and get no end of errors.  This is on hoary BTW.

Eclipse starts and appears to be working fine, but I probably get an "eclipse has messed up" dialogue box once evert 5 minutes on average.  Code completion fails all the time etc.

The same versions on i386 (obviously the 32 bit versions) work a treat (again on hoary).

Col

---

### Post by Nadir on 2005-02-25
[QUOTE=yatesco]All,
Eclipse starts and appears to be working fine, but I probably get an "eclipse has messed up" dialogue box once evert 5 minutes on average. Code completion fails all the time etc.
Col[/QUOTE]

Yes, it's a bug in the hotspot server VM for amd64. IBM's 1.4.2 VM for amd64 works ok.


Tristan

---

### Post by yatesco on 2005-02-25
I thought blackdown was IBM?  How do I get the IBM JDK?  Thanks.

---

