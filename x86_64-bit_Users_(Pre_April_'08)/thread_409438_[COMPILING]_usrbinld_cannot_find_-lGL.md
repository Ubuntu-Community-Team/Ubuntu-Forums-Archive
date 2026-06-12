---
title: "[COMPILING] /usr/bin/ld: cannot find -lGL"
date: 2007-04-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by nicoladimaria on 2007-04-14
I get this error while trying to compile mixxx
/usr/bin/ld: cannot find -lGL
probably it's just some linking issue, any idea ?
thanks

grazie

EDIT:
deleting /usr/lib/libGL.so
and doing```

cd /usr/lib/
sudo ln -s libGL.so.1.0.9755 libGL.so
```
did the trick

---

