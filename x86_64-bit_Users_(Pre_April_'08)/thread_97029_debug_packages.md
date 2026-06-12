---
title: "debug packages"
date: 2005-11-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by stimpie on 2005-11-30
My nautilus is crashing (constantly) with the error:
GLib-ERROR **: gmem.c:141: failed to allocate 375277062455712 bytes
aborting...

So I thought lets install some debug packages.

Alot of packages have no dbg package in my repositories and the nautilus-dbg says:
Depends: nautilus (=2.12.1-0ubuntu1) but 2.12.1-0ubuntu1.1 is to be installed

Any hints on how to find the cause of this bug?

---

### Post by stimpie on 2006-02-01
Issue is still occuring and I haven't found a solutions yet.  

I filed a bug report [http://bugzilla.gnome.org/show_bug.cgi?id=322386](http://bugzilla.gnome.org/show_bug.cgi?id=322386)

---

### Post by slavik on 2006-02-01
that is some serious bug ...

the error is that malloc() is trying to get that many bytes, which I don't think any computer has in RAM capacity (home computer) ... something gets miscalculated somewhere ...

I would post that to the gnome devs or in the gnome forum ...

---

