---
title: "Have I found a Bug with rdate?"
date: 2008-08-31
forum: x86 64-bit Users
---

### Post by ewtrowbr on 2008-08-31
I am a first time ubuntu user, recently come over from gentoo. I am extremely impressed thus far.

Trying to get rdate on the system...

```
ewtrowbr@strawbox:~$ sudo apt-get install rdate
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  rdate
0 upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
Need to get 16.0kB of archives.
After this operation, 81.9kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hardy/universe rdate 1:1.1.2-5 [16.0kB]
Fetched 449B in 0s (2122B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/r/rdate/rdate_1.1.2-5_amd64.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ewtrowbr@strawbox:~$

```

System is brand new, and the apt-get update did not help. I am not yet experienced enough with apt to troubleshoot intelligently... Any suggestions for getting rdate on the system?

Thanks,
erich

---

### Post by Jouke74 on 2008-09-01
Try another repository mirror.

---

### Post by insane_alien on 2008-09-01
your download was corrupted or cut off in the middle.

its not a bug with rdate itself. the gentoo equivalent would be if you cancelled the download of the source halfway through and then tried to install anyway without getting the complete source.

either keep trying, try a different server or find the package manually.

---

