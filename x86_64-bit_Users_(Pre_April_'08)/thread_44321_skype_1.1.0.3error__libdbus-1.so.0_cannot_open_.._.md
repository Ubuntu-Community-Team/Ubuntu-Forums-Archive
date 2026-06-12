---
title: "skype 1.1.0.3:error : libdbus-1.so.0: cannot open .. object"
date: 2005-06-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by gratefulfrog on 2005-06-25
Hi!

Running Ubuntu 5.04 on amd64, skype 1.0.0.7 works fine with QTstatic build, but I tried to install the latest skype 1.1.0.3, and now get:

> ./skype
./skype: error while loading shared libraries: libdbus-1.so.0: cannot open shared object file: No such file or directory

Note:
> ls /usr/lib/libdbus-1.so.0 -al
lrwxrwxrwx 1 root root 18 2005-04-08 20:49 /usr/lib/libdbus-1.so.0 -> libdbus-1.so.0.0.0

any ideas?

Any reason why skype shouldn't work out-of-the-box on Ubuntu 64 bit?

---

### Post by jerutley on 2005-06-25
First thing, you havent shown that the library its tripping on actually exists:

Note:
> ls /usr/lib/libdbus-1.so.0 -al
lrwxrwxrwx 1 root root 18 2005-04-08 20:49 /usr/lib/libdbus-1.so.0 -> libdbus-1.so.0.0.0

So libdbus-1.so.0 is a symlink to libdbus-1.so.0.0.0 - what is libdbus-1.so.0.0.0?  does it exist, or is it still a symlink to something else entirely.

That's going to be your starting point.

---

