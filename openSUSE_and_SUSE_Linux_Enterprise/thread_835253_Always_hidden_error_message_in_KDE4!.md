---
title: "Always hidden error message in KDE4!"
date: 2008-06-20
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Growbag on 2008-06-20
This has been happening since I first tried KDE4.

I get an eror sound just before the desktop appears, and sometimes I'm actually (on logout/crash etc') able to see a knotify window whining about a SIGDEV or something odd.

I managed to get this info from it:

```
[?1034h(no debugging symbols found)
----- snip -----
(no debugging symbols found)
(x10)
----- snip -----
[Thread debugging using libthread_db enabled]
[New Thread 0x7ff529d4b740 (LWP 4566)]
----- snip -----
(no debugging symbols found)
(x50)
----- snip -----
[KCrash handler]
#5  0x00007ff52ce5e5c5 in raise () from /lib64/libc.so.6
#6  0x00007ff52ce5fbb3 in abort () from /lib64/libc.so.6
#7  0x00007ff52ce9c3a8 in ?? () from /lib64/libc.so.6
#8  0x00007ff52cea1af8 in ?? () from /lib64/libc.so.6
#9  0x00007ff52cea3508 in ?? () from /lib64/libc.so.6
#10 0x00007ff52cea36e6 in free () from /lib64/libc.so.6
#11 0x00007ff53161df3d in ?? () from /usr/lib64/libQtCore.so.4
#12 0x00007ff531627809 in ?? () from /usr/lib64/libQtCore.so.4
#13 0x00007ff52ce6126d in exit () from /lib64/libc.so.6
#14 0x00007ff52ce4a43d in __libc_start_main () from /lib64/libc.so.6
#15 0x0000000000400879 in _start ()
#0  0x00007ff52cece261 in nanosleep () from /lib64/libc.so.6
```

Nobody on the suse forums seems to know, so any ideas welcome (apart from informing me that it's "some kind of error related to libc.so.6" of course ;)  ).

---

### Post by some-guy on 2008-06-20
> **Growbag said:**
> This has been happening since I first tried KDE4.

I get an eror sound just before the desktop appears, and sometimes I'm actually (on logout/crash etc') able to see a knotify window whining about a SIGDEV or something odd.

I managed to get this info from it:

```
[?1034h(no debugging symbols found)
----- snip -----
(no debugging symbols found)
(x10)
----- snip -----
[Thread debugging using libthread_db enabled]
[New Thread 0x7ff529d4b740 (LWP 4566)]
----- snip -----
(no debugging symbols found)
(x50)
----- snip -----
[KCrash handler]
#5  0x00007ff52ce5e5c5 in raise () from /lib64/libc.so.6
#6  0x00007ff52ce5fbb3 in abort () from /lib64/libc.so.6
#7  0x00007ff52ce9c3a8 in ?? () from /lib64/libc.so.6
#8  0x00007ff52cea1af8 in ?? () from /lib64/libc.so.6
#9  0x00007ff52cea3508 in ?? () from /lib64/libc.so.6
#10 0x00007ff52cea36e6 in free () from /lib64/libc.so.6
#11 0x00007ff53161df3d in ?? () from /usr/lib64/libQtCore.so.4
#12 0x00007ff531627809 in ?? () from /usr/lib64/libQtCore.so.4
#13 0x00007ff52ce6126d in exit () from /lib64/libc.so.6
#14 0x00007ff52ce4a43d in __libc_start_main () from /lib64/libc.so.6
#15 0x0000000000400879 in _start ()
#0  0x00007ff52cece261 in nanosleep () from /lib64/libc.so.6
```

Nobody on the suse forums seems to know, so any ideas welcome (apart from informing me that it's "some kind of error related to libc.so.6" of course ;)  ).
The only things I can think of are to reinstall glibc and qt

---

### Post by RedDwarf on 2008-06-21
You need to install debuginfo/debugsource packages to obtain a useful backtrace.

No KDE4 myself, so...

---

