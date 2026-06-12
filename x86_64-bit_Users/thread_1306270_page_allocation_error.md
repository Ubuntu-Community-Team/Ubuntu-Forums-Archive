---
title: "page allocation error"
date: 2009-10-30
forum: x86 64-bit Users
---

### Post by maxwevers on 2009-10-30
Hi,

lateley I get a lot of ```
page allocation failure. order:3, mode:0x4020
``` in the syslog caused by different processes.

Goggle came with various results but no good solution. Is is a bug in the kernel or is something wrong with my hardware?

---

### Post by lensman3 on 2009-10-30
Sounds like flaky hardware.  You might do a memory check.  Leave it running overnight and see if you flush out the memory  stick.

You might check how hot your CPU is running.  If the CPU is at running 100%, the CPU could fail occasionally, except I would expect the  CPU to lock the entire machine.

---

### Post by maxwevers on 2009-10-31
I will try the memtest, though regarding google this seems more like a bug in a kernel module (at least as far as I unstand the links).

I doubt that it is caused by an overheated CPU as it is mostly idle and the case is well vented.

---

