---
title: "Has anyone made xmms/bmp musepack plugins work?"
date: 2005-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pse on 2005-03-10
I was wondering if someone was successfuly using MPC plugins on AMD64, as I can't seem to make them work...this has been my hottest tip so far: [http://lists.freebsd.org/pipermail/freebsd-ports-bugs/2004-April/029974.html](http://lists.freebsd.org/pipermail/freebsd-ports-bugs/2004-April/029974.html)
Any ideas?

---

### Post by Pse on 2005-03-15
I can confirm MPC working on AMD64 as a XMMS plugin by manually compiling and using the -fPIC option. This thread is SOLVED!

[EDIT] A mod should add "[SOLVED]" to the thread title.

---

### Post by WMCoolmon on 2005-04-06
Er, any chance of getting it added to the apt repository?

---

### Post by negatory on 2005-04-12
I compiled it with no worries...
I just have one question regarding compiling the various sources....how can I had the -fPIC to a Makefile?I just added it to the CFLAGS tag but it didn't work.
Thanks.

Pedro Carrico

---

### Post by Gregi on 2005-04-20
[QUOTE=negatory]I compiled it with no worries...
I just have one question regarding compiling the various sources....how can I had the -fPIC to a Makefile?I just added it to the CFLAGS tag but it didn't work.
[/QUOTE]

It was impossible for me to compile bmp-musepack 1.1.2 from [www.musepack.net](www.musepack.net)
But i get the newest version from SVN Repository (same site) and everything goes fine.

---

