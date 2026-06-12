---
title: "How did I get a 64bit kernel?"
date: 2009-04-27
forum: x86 64-bit Users
---

### Post by vhenry on 2009-04-27
I originally downloaded and installed Intrepid and recently upgraded to 9.04 jaunty. I've been trying to install Aptana and discovered the problem is related to having a 64bit kernel.

Only I don't know how that happened. Any ideas how to get the correct, 32bit version installed?

I believe this command confirms I'm running 64 bit:

file /sbin/init
/sbin/init: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.8, stripped

---

### Post by ptn107 on 2009-04-27
```
uname -m
```
This command will confirm whether or not your using a 64-bit kernel.

---

### Post by vhenry on 2009-04-27
> **ptn107 said:**
> ```
uname -m
```
This command will confirm whether or not your using a 64-bit kernel.

Guess this confirms it: x86_64

Questions:

how can I make sure I get the 32 bit version? downloaded ubuntu 9.04-desktop-i386.iso, is this correct?
getting the 32 bit version will probably ensure I can run Aptana, but will it break anything else?
is the kernel version dependent upon the computer hardware at all?

---

### Post by ptn107 on 2009-04-27
If you downloaded _[ubuntu-9.04-desktop-i386.iso]("http://releases.ubuntu.com/jaunty/ubuntu-9.04-desktop-i386.iso")_ then your good to go.  Just install it.

---

