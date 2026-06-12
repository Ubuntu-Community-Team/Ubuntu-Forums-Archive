---
title: "Cannot compile 32-bit source: Mistakenly referencing 64-bit objects"
date: 2009-06-04
forum: x86 64-bit Users
---

### Post by mavaddat on 2009-06-04
I would like to compile a program from source in my 64-bit Ubuntu. This is the linking error I'm trying to get around:```
<<PARTIAL TERMINAL OUTPUT>>
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.4/../../../libgdbm.so when searching for -lgdbm
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.4/../../../libgdbm.a when searching for -lgdbm
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libgdbm.so when searching for -lgdbm
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libgdbm.a when searching for -lgdbm
/usr/bin/ld: skipping incompatible /usr/lib/libgdbm.so when searching for -lgdbm
/usr/bin/ld: skipping incompatible /usr/lib/libgdbm.a when searching for -lgdbm
/usr/bin/ld: cannot find -lgdbm
collect2: ld returned 1 exit status
make[1]: *** [obj/manager] Error 1
```

After some reading, it seemed that the safest bet is to set-up a 32-bit environment and *chroot* into it. To that end, I followed [the instructions here](http://ubuntuforums.org/showthread.php?t=24575) to no avail.

Is this the right way? If so, can someone tell me how to actually enter into the 32-bit environment? I've followed all the instructions, yet it is still utterly unclear how I run or compile 32-bit programs. I do ```
sudo chroot /chroot/
``` and run ```
uname -a
``` but all I get is ```
Linux mavaddat-desktop 2.6.24-23-generic #1 SMP Wed Apr 1 21:43:24 UTC 2009 x86_64 GNU/Linux
```. Doesn't this mean I'm not in a 32-bit environment?

It's all very frustrating. I just want a command line (shell) prompt that allows 32-bit compilation. (I know about the '-m32' flag in gcc, but my *make* depends on objects that are already pre-compiled as 64-bit).

**Thanks** to anyone who can help!!!!

---

