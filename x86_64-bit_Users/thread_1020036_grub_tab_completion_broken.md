---
title: "grub tab completion broken"
date: 2008-12-23
forum: x86 64-bit Users
---

### Post by ameno on 2008-12-23
hellas

my story is about the same as in this thread:
[https://listman.redhat.com/archives/rhl-list/2007-September/msg03328.html](https://listman.redhat.com/archives/rhl-list/2007-September/msg03328.html)

tabs, ^A etc dont work, but print the corresponding characters.

i dont think this would go unnoticed... is it really a bug?
can anyone confirm, that tab completion is not working in x64?
e.g. start "grub" and press tab

---

### Post by ameno on 2008-12-25
thanks for not helping! :P

it seems it IS a problem with amd64.. but not grub itself but a statically linked library.
see details in the but report [https://bugs.launchpad.net/bugs/282577](https://bugs.launchpad.net/bugs/282577)

---

### Post by sim909 on 2009-05-14
Your welcome, always glad to not help...

Just discovered that I have the same problem. It is somewhere suggested that installing the 32 bit version of grub on a 64 platform solves the issue, but I don't quite know how to do that...

---

