---
title: "how to check if my ubuntu is 32 or 64bit?"
date: 2006-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by drexvil on 2006-10-16
Sorry, very newbie on this...:(

---

### Post by taurus on 2006-10-16
From a terminal,

```
uname -a
```

---

### Post by drexvil on 2006-10-16
What's a terminal? Just kidding...:rolleyes: 

It outputs this:

Linux Server 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

So, by the 386, does it mean that it's 32bit?

---

### Post by incubus on 2006-10-16
Yes. More specifically, you're using a kernel compiled for i686.  In my case, for example, the output reads like this:

```

Linux <hostname> 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux

```

Note the "x86_64" part of it.  You may ask next: is it possible to upgrade?  While it may be in theory, I would strongly suggest a fresh install instead.  The binaries and libraries are compiled differently. : )

incubus

---

### Post by drexvil on 2006-10-16
Thanks! I wasn't actually planning to go 64-bit just yet, want to learn a bit of Linux beforehand. Hope this thread will help another newbie.

---

