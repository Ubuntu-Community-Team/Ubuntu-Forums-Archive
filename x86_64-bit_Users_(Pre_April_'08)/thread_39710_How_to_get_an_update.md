---
title: "How to get an update?"
date: 2005-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by daFool on 2005-06-06
I'm trying to print from Open Office but Open Office doesn't print and I can not set the printer setting as oopadmin crashes. A library update mentioned in closed [bug](https://bugzilla.ubuntu.com/show_bug.cgi?id=6762) would probably remove the crash. But where I can get that update and how?

> sudo apt-get install ia32-libs-gtk

Tells me that I already have to most recent libs but dpkg shows that I am still having version 3.

> Maintainer: Tollef Fog Heen <tfheen@canonical.com>
Architecture: amd64
Version: 3


---

### Post by daFool on 2005-06-06
By adding:

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

to apt.sources.list but althought it stops crashing of oopadmin it doesn't enable printing.
 ](*,)

---

