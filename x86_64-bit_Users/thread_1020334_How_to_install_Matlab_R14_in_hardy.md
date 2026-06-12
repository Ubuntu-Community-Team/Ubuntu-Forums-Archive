---
title: "How to install Matlab R14 in hardy"
date: 2008-12-24
forum: x86 64-bit Users
---

### Post by wangjiajun on 2008-12-24
Dear all,

Merry Christmas to everyone of you. 

I have a copy of Matlab (R14) which I successfully installed in 32bit linux system. 

After switching to Hardy, I can not install it. 

When I run install script file on the CD, I see the following error:

cp: cannot stat `/media/iso/1/update/bin/glnxa64/*': No such file or directory
Error writing to /tmp/6835tmwinstall
The installer is unable to copy files to /tmp.
Make sure that /tmp exists, is writable, and has
at least 5 megabytes of available space.

Can someone help me install it?


Thanks!

---

### Post by soxs on 2008-12-24
What version of matlab do you own? I own 7.7.04 blah R2008b and it worked pretty fine.

---

### Post by Nepherte on 2008-12-24
Try to copy the whole dvd content to /tmp and run the installer from /tmp afterwards.

---

### Post by wangjiajun on 2008-12-24
> **Nepherte said:**
> Try to copy the whole dvd content to /tmp and run the installer from /tmp afterwards.

I tried that, still the same error. 

Looking at that error, the installer is right. 

There is indeed NO update/bin/glnxa64 directory, what I have is a directory named glnx86. 

I do not know why the installer ask for glnxa64 directory. Does that mean the version I have does not support AMD64?

---

### Post by wangjiajun on 2008-12-24
> **soxs said:**
> What version of matlab do you own? I own 7.7.04 blah R2008b and it worked pretty fine.

It says R14. 

It worked fine with my old 32 bit Linux, however gives me hard time on my 64bit Hardy.

---

