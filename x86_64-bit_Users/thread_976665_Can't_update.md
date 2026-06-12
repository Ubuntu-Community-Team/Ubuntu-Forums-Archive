---
title: "Can't update"
date: 2008-11-09
forum: x86 64-bit Users
---

### Post by Torqumada286 on 2008-11-09
I have updraded from 8.04 to 8.10.  I am running into a few problems with the automatic updates.  I get the following error message:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Exactly how do I go about doing this?

Torqumada

---

### Post by DrDagostino1 on 2008-11-09
From what I can see, running:
```

dpkg --configure -a

```
in Terminal should fix the problem.

---

### Post by Torqumada286 on 2008-11-09
Thank you.

Torqumada

---

