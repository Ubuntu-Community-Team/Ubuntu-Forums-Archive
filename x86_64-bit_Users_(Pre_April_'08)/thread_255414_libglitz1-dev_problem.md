---
title: "libglitz1-dev problem"
date: 2006-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by coldsoul on 2006-09-11
Hi! I was installing DC++ on my dapper drake ubuntu on amd64 following this how-to: [http://ubuntuforums.org/showthread.php?t=28378](http://ubuntuforums.org/showthread.php?t=28378)
i got it running... but i got an error after installing the packages described in the how to. no i get an error every time i want to install something:
```

Unpacking libglitz1-dev (from .../libglitz1-dev_0.5.6-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libglitz1-dev_0.5.6-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libglitz.la', which is also in package glitz-cvs
Errors were encountered while processing:
 /var/cache/apt/archives/libglitz1-dev_0.5.6-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Can someone help me solve this issue please!

---

### Post by coldsoul on 2006-09-11
hm i installed it with --force option and it worked. sorry to bother you

---

