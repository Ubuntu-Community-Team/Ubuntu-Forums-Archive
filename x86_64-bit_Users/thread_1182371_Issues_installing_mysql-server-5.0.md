---
title: "Issues installing mysql-server-5.0"
date: 2009-06-08
forum: x86 64-bit Users
---

### Post by jbcurtin on 2009-06-08
Hey all,

  I am having issues installing the package specified in the above listing. Are others having issues with the package? Also, I have attempted to purge it via aptitude purge however I am still unsuccessful. 

 Here is some general output...

```

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```


Well I am in the process of replacing file from a working instance, however before I started looking into it. I wondered if there was even a init script...and guess what there isn't.

 Is anyone else having issues with this package?

amd64 9.04 
Gateway FX Laptop

Thanks,

---

### Post by Quasaur on 2009-06-24
I've filed a bug report: [387580]("https://bugs.launchpad.net/bugs/387580")

---

