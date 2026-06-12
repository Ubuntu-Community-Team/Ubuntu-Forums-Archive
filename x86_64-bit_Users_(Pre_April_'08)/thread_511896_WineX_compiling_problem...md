---
title: "WineX compiling problem.."
date: 2007-07-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Myzrael on 2007-07-28
Hey everyone. Trying to install the WineX from CVS right now using a script. Script runs well....dependencies should be good. Upon making I get this.....(more text but this is the important part)

/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed.

So I have a problem there........Any tips?

---

### Post by Myzrael on 2007-07-28
STATUS : FIXED!

Needed a few symlinks extra :)

---

