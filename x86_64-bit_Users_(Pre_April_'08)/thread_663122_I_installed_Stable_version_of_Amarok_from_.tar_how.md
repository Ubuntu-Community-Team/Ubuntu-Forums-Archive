---
title: "I installed Stable version of Amarok from .tar how do I remove it"
date: 2008-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lukasz Tarkowski on 2008-01-09
Dear suoport
I installed Amarok stable version from _./configure_ and I would like to know how I can remove it

---

### Post by Lukasz Tarkowski on 2008-01-09
Problem Solved
Install from Apt-get on top of Stable version and then remove

---

### Post by harold4 on 2008-01-09
You can also run make uninstall  from inside the src extracted from the .tar.

Take a look at checkinstall.   Instead of running make install, you can run checkinstall -D.  That way it is manageable in apt.

---

### Post by Lukasz Tarkowski on 2008-01-09
Thank You harold4

---

