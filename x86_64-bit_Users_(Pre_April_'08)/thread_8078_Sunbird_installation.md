---
title: "Sunbird installation"
date: 2004-12-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Gataca on 2004-12-14
distro : Ubuntu amd64

I installed sunbird calendar application on my PC.
When I try to run it( with ./sunbird), this error message appears :
```

./sunbird-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
``` 

In do not anderstand why such error because when I look into the /usr/lib/ directory the file libgtk-x11-2.0.so.0 exists.
see part of the contents of my /usr/lib/ directory
```
................................
lrwxrwxrwx    1 root     root           26 2004-11-09 17:52 libgtk-x11-2.0.so.0 -> libgtk-x11-2.0.so.0.400.10
-rw-r--r--    1 root     root      3117680 2004-09-22 18:13 libgtk-x11-2.0.so.0.400.10
..................................
``` 

When I look in the /usr/ directory I can see 3 types of "lib" directory :
```
drwxr-xr-x  104 root     root        20480 2004-12-14 09:41 lib
drwxr-xr-x    7 root     root         4096 2004-12-10 14:46 lib32
lrwxrwxrwx    1 root     root            3 2004-11-09 18:15 lib64 -> lib
``` 

Is this the root of my problem ?

Any ideas ?

---

