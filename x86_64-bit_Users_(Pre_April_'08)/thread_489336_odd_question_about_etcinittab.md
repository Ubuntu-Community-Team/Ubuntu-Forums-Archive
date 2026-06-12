---
title: "odd question about /etc/inittab"
date: 2007-07-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by praxis22 on 2007-07-01
Hi,

I don't appear to have an /etc/inittab,  yet my system functions completely normally. /sbin/init is running as process 1 and many other processes have a parent process ID of 1, so obviously it is starting other processes. I've had a trawl through my system, and all I can find is one example of how you would add another program to inittab. anyone else have this too?

---

### Post by John.Michael.Kane on 2007-07-01
This may help [http://ubuntuforums.org/showthread.php?t=292507](http://ubuntuforums.org/showthread.php?t=292507)

---

### Post by praxis22 on 2007-07-01
New avatar eh?

Thanks. I knew I was dealing with upstart, but I habitually jump past the first page of man output, so I can look at the switches and files, which was a bit of a liability in this case, as it tells you front and center where the files are located.

Doh! :)

---

