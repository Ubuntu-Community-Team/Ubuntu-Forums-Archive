---
title: "Wing IDE 3.1 will not install on 64bit Athlon Ubuntu 8.10"
date: 2009-02-03
forum: x86 64-bit Users
---

### Post by yyz53 on 2009-02-03
I have just loaded up my new system (Athlon 5000 with 4 Gb RAM on a GigaByte M78 motherboard) and when I try to install Wing 101 the package installer stops with a error:Wrong Architecture 'i386'.

I am pretty new to Linux.  Is there something I ma doing wrong?

---

### Post by sanderj on 2009-02-03
Is the Wing IDE the python IDE?

If so: they are offering a i386 deb(see [ftp://wingware.com/pub/wingide-101/3.1.7/](ftp://wingware.com/pub/wingide-101/3.1.7/)), whereas you're running x86_64/amd64 Ubuntu and you thus an amd64 deb.

Solutions:
1) ask Wing to provide a x86_64/amd64 deb version
2) find the tool ("getdeb", "getlib", "libdeb"?) that will install the needed i386-libraries
3) get wingide-101-3.1.7-1-i386-linux.tar.gz and see if that works (after unpacking)

PS: strange: the release notes say 64-bit should be ok:
> System requirements are ... a recent Linux system (either 32 or 64 bit).
Wing IDE 3.1 supports Python versions 2.0.x through 2.5.x.

---

### Post by yyz53 on 2009-02-03
Thanks Sanderj.

Installing from the tar using the py installer worked fine.

---

