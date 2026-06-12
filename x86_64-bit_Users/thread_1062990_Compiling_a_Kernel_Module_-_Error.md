---
title: "Compiling a Kernel Module - Error"
date: 2009-02-07
forum: x86 64-bit Users
---

### Post by Quantumstate on 2009-02-07
Trying to compile lirc_imontouch module so I can get my touchscreen working, but it gives an error that doesn't make sense:

```
/home/bill/dl/lirc_imontouch-0.1b/lirc_imontouch.c:46:29: error: drivers/kcompat.h: No such file or directory                                                   
/home/bill/dl/lirc_imontouch-0.1b/lirc_imontouch.c:47:26: error: drivers/lirc.h: No such file or directory
```

Well the module source is in my user directory, but {source}/drivers/kcompat.h  and lirc.h certainly are there.  They are symlinks that link to the actual files in the next directory up, and those files are there. 

I've tried echoing what it thinks SUBDIRS is, but bash commands do not seem to work in a makefile.

Here's what the Makefile has:
```
MDIR = drivers/misc

EXTRA_CFLAGS = -DEXPORT_SYMTAB
KBUILD_CFLAGS += -DIRCTL_DEV_MAJOR=61
CURRENT = $(shell uname -r)
KDIR = /lib/modules/$(CURRENT)/build
PWD = $(shell pwd)
DEST = /lib/modules/$(CURRENT)/kernel/$(MDIR)

obj-m      := lirc_dev.o lirc_imontouch.o

default:
	make -C $(KDIR) SUBDIRS=$(PWD) modules

install:
	su -c "cp -v lirc_imontouch.ko lirc_dev.ko $(DEST) && /sbin/depmod -a"

clean:
	-rm -f *.o *.ko .*.cmd .*.flags *.mod.c

-include $(KDIR)/Rules.make
```

BTW, there is no drivers/misc directory in the source, if that matters.

---

### Post by cariboo on 2009-02-07
Have you got build-essential installed, becuase it looks like you are missing kernel-headers.

Jim

---

### Post by Quantumstate on 2009-02-07
Yep, have build-essentials, linux-headers, and in fact am booted to a custom kernel that I'd compiled myself.

It's looking in a 'drivers' directory for those files, and that 'drivers' directory is there in the source tree with those files, so the compiler must not be looking there.  I can't imagine where else it could be looking though, and I can't make it tell me.

---

### Post by Quantumstate on 2009-02-09
Oh man, you mean nobody knows how the module compile system works?

---

### Post by Yellow Pasque on 2009-02-09
Is it possible that you need to install another lirc-related package like lirc-modules-source or something else: [http://packages.ubuntu.com/search?keywords=lirc&searchon=names&suite=intrepid&section=all](http://packages.ubuntu.com/search?keywords=lirc&searchon=names&suite=intrepid&section=all)

---

### Post by Yellow Pasque on 2009-02-09
> in fact am booted to a custom kernel
How did you install this kernel and where do you have the source for it?

---

### Post by Quantumstate on 2009-02-09
Thanks Temüjin, but I've been advised in the Debian forum:

> Open lirc_imontouch.c in your favorite editor o change lines 46-48 
 
Code:

   #include <drivers/kcompat.h> 
 #include <drivers/lirc.h> 
 #include <drivers/lirc_dev/lirc_dev.h> 
 
   
 to 
 
Code:

   #include "drivers/kcompat.h" 
 #include "drivers/lirc.h" 
 #include "drivers/lirc_dev/lirc_dev.h" 
... and it works!

---

