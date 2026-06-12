---
title: "How to get libstdc++-libc6.2-2.so.3 working for 32bit apps in Ubuntu 8.04.1 x86_64"
date: 2008-10-18
forum: x86 64-bit Users
---

### Post by r2rX on 2008-10-18
Greetz guys. :)

Well, i'm running Ubuntu v8.04.1 x86_64, and i'm enjoying it thus far. The only issue, however, is that there are some 32bit applications which refuse to run unless libstdc++-libc6.2-2.so.3 is installed.

From my research so far, i've not managed to figure out exactly how to get it and get it working.

Any tips/advice?

I appreciate it plenty. :)

r2rX  :D

---

### Post by istblacken on 2008-10-18
you can get 32 bit (i386) deb for that package. then open it with archive manager and extract the contents of the data.tar.gz into the /usr/lib32. try this maybe this will work :)

---

### Post by Yellow Pasque on 2008-10-18
Use getlibs for 32-bit libraries. [http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs](http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs)

---

### Post by r2rX on 2008-10-23
Sorry for such a late reply...but it's working beautifully now.

Installed getLibs and used

```
sudo dpkg -i --force-all libstdc++2.10-glibc2.2_2.95.4-24_i386.deb
```

I'm so jazzed. :p

Cheers guys.

r2rX  :D

---

