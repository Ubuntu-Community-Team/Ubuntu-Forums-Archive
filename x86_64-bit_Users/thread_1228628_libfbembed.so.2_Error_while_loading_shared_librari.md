---
title: "libfbembed.so.2 Error while loading shared libraries"
date: 2009-08-01
forum: x86 64-bit Users
---

### Post by latev on 2009-08-01
I'm trying to get Virtual Volumes View going on my Ubuntu 64 system. Unfortunately there's no x64 bit version of vvv available so I'm running the x32 one. It complains about not finding the libfbembed.so.2 shared library, however mlocate reports
tl@I7:~/TL-VVV-1.0$ mlocate libfbembed.so
/usr/lib/libfbembed.so.2
/usr/lib/libfbembed.so.2.0.4

..so - it's there

My guess is the installed version is probably x64 and I need a x32 bit version for the vvv app.
The question - how & where do I find one?
How do I install it manually?

Thanks in advance

---

