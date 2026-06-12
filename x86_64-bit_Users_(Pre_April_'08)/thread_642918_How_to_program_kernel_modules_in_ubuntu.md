---
title: "How to program kernel modules in ubuntu"
date: 2007-12-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by thejdev on 2007-12-17
Hi i have a AMD64 comp that does not have an internet connection
I have installed Ubuntu 7.1 and have installed the build-essential packages for libc6-dev,gcc and g++ (which come along with the live CD). I tried to program a simple 'hello world' kernel module but several header files were missing in /usr/include . I downloaded these from the ubuntu website but the modules still dont run . Could someone help me patch this out

---

### Post by rasta_freak on 2007-12-17
You must have kernel-headers (& company) package(s) installed, and you must tell compiler "-I/usr/src/linux-headers-2.6.22-14" (so that is uses that includes over those in /usr/include).

EDIT:
Sorry, packages are named: "linux-headers-2.6..."

---

