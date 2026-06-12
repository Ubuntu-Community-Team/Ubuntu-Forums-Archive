---
title: "Ubuntu AMD 64 State of the Union"
date: 2005-06-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by joey on 2005-06-09
Greetings,

I'm migrating off of the PPC platform and on to an AMD 64 system running Ubuntu.  From reading the forum posts it seems that the Hoary AMD 64 load runs about 80% of the applications that are available for AMD 32 (not due to Ubuntu but due to the programs themselves).

Three questions:

1) Is the above correct?

2) Is there a known "does not play nice with AMD 64" list? If not perhaps we can start one and make it sticky.

3) Any ideas (besides a complicated chroot environment) on how to run a 64 kernel without sacrificing much?

I'm currently planning on running the 32 Kernel until 64 matures a bit more.

Thanks!

Joey

---

### Post by Gnobody on 2005-06-10
You can run EVERY i386 application in a 32-bit chroot but you will really only need Firefox, Flash, Java, and at this very moment OpenOffice.org2 (an amd64 build will be availible any day)  Also some commerical games also need a chroot but there are many ways around that.  So you can run 100% of the software out there but it will take a tad bit extra work.

---

### Post by gratefulfrog on 2005-06-10
Well I can't get either of the standard Common Lisp environments to work on 64 bit Ubutunu:

cmucl and sbcl both behave badly under both 64bit, and even under a 32 bit  chroot.

transcode can't be compiled for 64 bit, I  don't know if it will run on 32 bit chroot.

Ciao,
GF

---

### Post by ollipekka on 2005-06-11
x86_64 version of Ubuntu runs fine if you do not need WMV / WMA or any other proprietary software. 

Most stuff I run and do are just fine. No unneccesary tweaking is required and you are good to go after the installation cd pops out.

---

