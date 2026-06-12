---
title: "UML - Compiling error"
date: 2005-05-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by daniele on 2005-05-02
Hi all,

I've been trying to compile UML on my AMD64 for several days, but with no success.
I downloaded the kernel **linux-2.6.4.tar.bz2**
Afterwards, from official UML web-site I downloaded the following packages

**uml-patch-2.6.4-1.bz2**
**uml-patch-x86-64-2.6.4.bz2**

Then I unpacked the kernel, and applied the patches in the following way (as the their ChangeLog says: **[http://user-mode-linux.sourceforge.net/changelog-uml-patch-x86-64-2.6.4.bz2.html](http://user-mode-linux.sourceforge.net/changelog-uml-patch-x86-64-2.6.4.bz2.html)**)

$ bzcat uml-patch-2.6.4-1.bz2 | patch -p1
$ bzcat uml-patch-x86-64-2.6.4.bz2 | patch -p1

After configuring 
  **make config ARCH=um**
and compiling
  **make linux ARCH=um**
I always get this error :

[B]arch/um/kernel/ksyms.c:91: error: `dump_thread' undeclared here (not in a function)
arch/um/kernel/ksyms.c:91: error: initializer element is not constant
arch/um/kernel/ksyms.c:91: error: (near initialization for `__ksymtab_dump_thread.value')
arch/um/kernel/ksyms.c:91: error: __ksymtab_dump_thread causes a section type conflict
make[1]: *** [arch/um/kernel/ksyms.o] Error 1
make: *** [arch/um/kernel] Error 2[/B]

Can anyone help me ?

Thanks in advance

daniele

---

