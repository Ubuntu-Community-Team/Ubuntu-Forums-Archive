---
title: "Can I run a 64bit application on 32bit linux?"
date: 2008-07-09
forum: x86 64-bit Users
---

### Post by JiminSD on 2008-07-09
The app doesn't really use the OS at all, only 64bit data structures and addressing.

Thanks

---

### Post by Yellow Pasque on 2008-07-09
You probably could through virtualization, but it won't work on an x86 install itself.

---

### Post by OmegaBLK on 2008-07-09
No, you cannot run a 64-bit application in a 32-bit operating system.  Nor, will it not work with virtualization either.  You need a 64-bit OS (virtualized or not) to run a 64-bit app period.

---

### Post by stchman on 2008-07-09
> **JiminSD said:**
> The app doesn't really use the OS at all, only 64bit data structures and addressing.

Thanks

If the app was written and compiled using 64 bit the pointers and arrays will be too large, so NO.

---

