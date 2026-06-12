---
title: "Problem about the kernel"
date: 2009-10-23
forum: x86 64-bit Users
---

### Post by linghai on 2009-10-23
Now I'm using The Ubuntu 9.04 
When I Downloaded a package of linux source(Version 2.6.28-11 ) and then I configured it without any changes.
And then,I typed the command like this "make" or "make bzImage"
The error appeared.Following is the error information.

linghai@linghai:/usr/src/linux-headers-2.6.28-11-generic$ sudo make bzImage
scripts/kconfig/conf -s arch/x86/Kconfig
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[1]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make: *** [prepare0] Error 2


I tried many ways, but the error still.
So I hope someone would help me to resolve it.
Thanks! And I wait for your answer.

---

### Post by masux594 on 2009-10-23
Use the [Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158") for all the indications about kernels..And maybe try to install le lastest one =), i've kernel 2.6.31 and it runs very well!

Sysc, A

---

### Post by inertz on 2009-10-23
Did the kernel source is already installed? Or you just download the kernel headers?

---

### Post by anubhavrocks on 2009-10-23
> **linghai said:**
> Now I'm using The Ubuntu 9.04 
When I Downloaded a package of linux source(Version 2.6.28-11 ) and then I configured it without any changes.
And then,I typed the command like this "make" or "make bzImage"
The error appeared.Following is the error information.

linghai@linghai:/usr/src/linux-headers-2.6.28-11-generic$ sudo make bzImage
scripts/kconfig/conf -s arch/x86/Kconfig
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[1]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make: *** [prepare0] Error 2


I tried many ways, but the error still.
So I hope someone would help me to resolve it.
Thanks! And I wait for your answer.
You need complete sources to compile the kernel.Also "sudo" is not required to compile sources.

---

### Post by linghai on 2009-10-24
Thanks all of your answers.

---

