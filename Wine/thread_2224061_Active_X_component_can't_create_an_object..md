---
title: "Active X component can't create an object."
date: 2014-05-14
forum: Wine
---

### Post by paul1945 on 2014-05-14
Installed Ubuntu 14.04 as a clean install because the upgrade from 13.10 failed, and found that the "MIMS Supplement 2013" a Windows based Australian medical drug guide I had previously installed on Ubuntu 13.10, on which it ran OK, now refuses to run and comes up with:
```
Active X component can't create an object
```
and then exits.  
I have installed all the Visual Basic packages on wine as well as the .net frameworks: 2.0, 2sp1, 3.0, 3sp1, 3.5 and 4.0.
I am totally baffled by this, any help would be greatly appreciated.

---

### Post by QIII on 2014-05-14
Hello!

Often that message appears with a colon followed by the control or component that cannot be created.  Is that being reported?

---

### Post by paul1945 on 2014-05-14
> **QIII said:**
> Often that message appears with a colon followed by the control or component that cannot be created.  Is that being reported?
Hello QIII, no, no such information appears, just a box with that exact statement. 
But what I failed to mention because I thought it was not related to this was the fact that when the programs boot logo comes up first, the following warning appears:
```
error detecting number of users: 3706
Provider cannot be found. It may not be properly installed.
```
I thought that perhaps this was a simple matter of a missing module or .dll file in wine, but it looks like I am wrong, there is more involved here.
I have installed, uninstalled and reinstalled this program four times, but that seems to have changed nothing.
Regards, Paul.

---

