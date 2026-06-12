---
title: "What programming languages used the most, to develop Linux  App. ?"
date: 2009-01-02
forum: x86 64-bit Users
---

### Post by lse123 on 2009-01-02
What programming languages used the most, to develop Linux [eg kubuntu] Applications ? What for 64bit mainly applications ?

---

### Post by nemilar on 2009-01-02
A very interesting question... no real easy answer.

Linux (the kernel) and most of the core utilities are written in C.  Many, many programs are written in C or C++.  I'd be willing to bet that those are the two most common languages.

More and more common you will find applications written in Python (e.g, Deluge, Exaile, etc) as well as some system stuff (I think apt is in Python?  I know Yum is... as is the redhat installer, etc...)

---

### Post by MighMoS on 2009-01-03
Most Linux programs that don't do any sort of tricky memory management (VMs, etc) run just fine in both 32 and 64 bit machines, all that's needed is a recompile.

Most of the underlying "core" code of the system is written in C. Ubuntu however, uses python for most of its system maintenance scripts and custom software. You said [Kubuntu], so most of your programs that you'll interact with are written in C++ (with the QT library).

---

