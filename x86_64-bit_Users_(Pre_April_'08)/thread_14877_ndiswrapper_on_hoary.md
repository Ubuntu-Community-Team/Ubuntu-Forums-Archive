---
title: "ndiswrapper on hoary"
date: 2005-02-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by dt22 on 2005-02-10
Hello,

I've just installed latest release of hoary using the 2.6.10-2 kernel I believe and I can't get the ndiswrapper module to load.
It compiles fine but I can't modprobe it.  Has anybody had any success doing this?

I've tried ndiswrapper 1.0-rc4 and 1.1-rc1 with no luck.


Any help would be appreciated.


Thanks

David

---

### Post by blinksilver on 2005-02-11
RC4 worked for me, i am currently using 1.0, but 1.1RC1 panics my kernel, what wireless card are you using?

---

### Post by dt22 on 2005-02-12
Solved now, I was being an idiot!!

I forgot to run ndiswrapper -i before trying to modprobe it.  Thanks for replying though.



David

---

### Post by blinksilver on 2005-02-12
hey it happens to the best of us,

---

