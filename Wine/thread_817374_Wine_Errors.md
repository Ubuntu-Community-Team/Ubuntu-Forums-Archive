---
title: "Wine Errors"
date: 2008-06-03
forum: Wine
---

### Post by Margueritte on 2008-06-03
I have just installed Wine 1.0. My applications installed correctly to the correct directory.  Unfortunately, my application does not start, I receive the following error 
Cannot start DOS application  because vm86 mode is not supported on this platform.

Any suggestions, I am using Ubuntu 8.04 Intel 64.

Thank you

---

### Post by cogadh on 2008-06-03
You are probably getting the preloader problem. There's a fix here:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

### Post by Margueritte on 2008-06-03
No, I have already sorted out the Preloader problem.

---

### Post by Akria on 2008-06-09
You're trying to run 16-bit software, yes?
The problem is that vm86 is basically 32-bit emulation of 16-bit. x86-64 platforms, i.e. your 64-bit Ubuntu, don't support this emulation mode.
The only way you'll get around it is either to install 32-bit Ubuntu and dual-boot or make a virtual machine running a 32-bit guest operating system. Or, better yet, 16-bit so that you can run the app natively.

---

### Post by doorknob60 on 2008-06-09
If it's a DOS program, use DosBox.

---

