---
title: "32-Bit or 64-Bit?"
date: 2007-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by suttles95 on 2007-12-16
I have a dumb question...

How can I tell if I'm running Gutsy Gibbon 7.10 32-bit or 64-bit?

--Brian

---

### Post by Existentialist on 2007-12-16
Run:

>uname -a

x86_64 is 64 bit

---

### Post by Melcar on 2007-12-17
Run in the terminal:

uname -r -m


That will give you your current kernel version and the extension (x86_64 for 64bit).

---

