---
title: "opera for 64 bit-error"
date: 2008-05-28
forum: x86 64-bit Users
---

### Post by neerajkumar on 2008-05-28
after installing opera,when i run it in terminal i get the following error.

> neeraj@neeraj-desktop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.27-20080331.6/opera: error while loading shared libraries: libqt-mt.so.3: wrong ELF class: ELFCLASS64

can some1 help me?

---

### Post by Sef on 2008-05-28
Moved to x86 64-bit Users.

Have you tried the [64-bit deb beta]("http://snapshot.opera.com/unix/snapshot-1983/x86_64-linux/")?

---

### Post by Trindol on 2008-05-28
Your problem stems from the fact that you are trying to run 32bit opera on a 64 bit system. I'm not really sure beyond that. Someone else can probably get it to work, however it would be much easier to just download a deb file of 64 bit opera.

[http://snapshot.opera.com/unix/snapshot-1983/x86_64-linux/](http://snapshot.opera.com/unix/snapshot-1983/x86_64-linux/)

---

