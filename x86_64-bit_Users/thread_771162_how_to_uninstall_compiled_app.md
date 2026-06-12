---
title: "how to uninstall compiled app"
date: 2008-04-27
forum: x86 64-bit Users
---

### Post by inphektion on 2008-04-27
When you install something via ./configure ; make; make install
for example my awn 2.6, how do you then uninstall it if you want to get rid of it or install it via a package manager?  make uninstall?

---

### Post by milosz.galazka on 2008-04-27
It depends. You should read Makefile in source directory to find answer.
It could be *make uninstall*,*make remove* or maybe project has no uninstall script. If it doesn't provide simple way to remove itself then just look at Makefile to find which files are copied in which places.

---

### Post by inphektion on 2008-04-27
thanks.  makes sense.

---

