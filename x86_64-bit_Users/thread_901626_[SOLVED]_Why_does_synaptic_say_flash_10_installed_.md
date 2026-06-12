---
title: "[SOLVED] Why does synaptic say flash 10 installed when plugins report version 9"
date: 2008-08-26
forum: x86 64-bit Users
---

### Post by philinux on 2008-08-26
Anybody know why?

---

### Post by philinux on 2008-08-26
Just double checked synaptic versions.

Whats with the +really9.0.124

---

### Post by Yellow Pasque on 2008-08-26
...
> Changelog

flashplugin-nonfree (10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2) hardy-backports; urgency=low

  * **Upload Hardy release version to hardy-backports to undo a bad backport**
    - See LP 235135 for details


---

### Post by IanW on 2008-08-27
The genuine Flash10 release was badly b0rked.
To remove it from the repos safely, the devs posted a copy of v9.0.124 with a higher version number than v10.

---

### Post by philinux on 2008-08-27
That explains it then. Cheers

---

