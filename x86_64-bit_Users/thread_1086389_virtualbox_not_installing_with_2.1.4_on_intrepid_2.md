---
title: "virtualbox not installing with 2.1.4 on intrepid 2.6.11-generic"
date: 2009-03-04
forum: x86 64-bit Users
---

### Post by dramenard on 2009-03-04
Hello Everyone,

I have been using Virtualbox for a long time with different versions of Ubuntu. Since 2.1.4, I got this problem of not being able to use it anymore on kernel 2.6.11-generic. I think I've done everything suggested in the manual and in different posts I read(more than once...).

here is the content of vbox-install.log:

Attempting to install using DKMS
  removing old DKMS module vboxdrv version 

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 2.1.4
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/2.1.4/source ->
                 /usr/src/vboxdrv-2.1.4

DKMS: add Completed.

Preparing kernel 2.6.27-11-generic for module build:
(This is not compiling a kernel, just preparing kernel symbols)
Storing current .config to be restored when complete
using presented .config
make oldconfig....
make prepare....(bad exit status: 2)

Building module:
cleaning build area....
make KERNELRELEASE=2.6.27-11-generic -C /lib/modules/2.6.27-11-generic/build M=/var/lib/dkms/vboxdrv/2.1.4/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.27-11-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/vboxdrv/2.1.4/build/ for more information.
Failed to install using DKMS, attempting to install without
Makefile:154: *** Error: /usr/src/linux (version 2.6.27.10) does not match the current kernel (version 2.6.27-11-generic).  Stop.

AND here is the content of DKMS make.log regarding vbox 2.1.4:

DKMS make.log for vboxdrv-2.1.4 for kernel 2.6.27-11-generic (x86_64)
Tue Mar  3 23:49:01 EST 2009
make: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.27-11-generic/Module.symvers
           is missing; modules will have no dependencies and modversions.

  LD      /var/lib/dkms/vboxdrv/2.1.4/build/built-in.o
  CC [M]  /var/lib/dkms/vboxdrv/2.1.4/build/linux/SUPDrv-linux.o
In file included from include/linux/gfp.h:4,
                 from include/linux/slab.h:12,
                 from /var/lib/dkms/vboxdrv/2.1.4/build/linux/../SUPDrvInternal.h:99,
                 from /var/lib/dkms/vboxdrv/2.1.4/build/linux/SUPDrv-linux.c:37:
include/linux/mmzone.h:18:26: error: linux/bounds.h: No such file or directory
include/linux/mmzone.h:197:5: warning: "MAX_NR_ZONES" is not defined
In file included from include/linux/gfp.h:4,
                 from include/linux/slab.h:12,
                 from /var/lib/dkms/vboxdrv/2.1.4/build/linux/../SUPDrvInternal.h:99,
                 from /var/lib/dkms/vboxdrv/2.1.4/build/linux/SUPDrv-linux.c:37:
include/linux/mmzone.h:218: error: &#8216;MAX_NR_ZONES&#8217; undeclared here (not in a function)
In file included from /var/lib/dkms/vboxdrv/2.1.4/build/r0drv/linux/the-linux-kernel.h:80,
                 from /var/lib/dkms/vboxdrv/2.1.4/build/linux/SUPDrv-linux.c:38:
include/linux/mm.h:438:63: warning: "NR_PAGEFLAGS" is not defined
include/linux/mm.h:486:62: warning: "NR_PAGEFLAGS" is not defined
make[1]: *** [/var/lib/dkms/vboxdrv/2.1.4/build/linux/SUPDrv-linux.o] Error 1
make: *** [_module_/var/lib/dkms/vboxdrv/2.1.4/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'


The kernel-headers are the right one and I cannot go any further.

This is beyond my knowledge...

Can someone help?

Thank you

dramenard

---

### Post by 3Miro on 2009-03-04
Are you compiling this thing or installing it from a .deb. I just use the reps for the open source version or download the deb from the web-page.

What does make.log say? That seems to be the first error that you get.

---

### Post by marcelkoopman on 2009-03-04
You can also try the following:

```

sudo rm /usr/src/linux
sudo ln -s /usr/src/linux-headers-2.6.27-11-generic /usr/src/linux

```

What is does is remove the symbolic linux /usr/src/linux (pointing to  different kernel headers) and make a new one.

---

### Post by dramenard on 2009-03-04
Thank you 3Miro for answering,

I use the .deb and make.log is in my first post.

dramenard

---

### Post by dramenard on 2009-03-04
Thanks for attention marcelkoopman,

I did these command several times and I've just tried them again just in case:

root@acerlaptop:/home/andre# rm /usr/src/linux
root@acerlaptop:/home/andre# ln -s /usr/src/linux-headers-2.6.27-11-generic /usr/src/linux
root@acerlaptop:/home/andre# /etc/init.d/vboxdrv setup * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong
root@acerlaptop:/home/andre# 

dramenard

---

### Post by marcelkoopman on 2009-03-04
> **dramenard said:**
> Thanks for attention marcelkoopman,

I did these command several times and I've just tried them again just in case:

root@acerlaptop:/home/andre# rm /usr/src/linux
root@acerlaptop:/home/andre# ln -s /usr/src/linux-headers-2.6.27-11-generic /usr/src/linux
root@acerlaptop:/home/andre# /etc/init.d/vboxdrv setup * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong
root@acerlaptop:/home/andre# 

dramenard

What does /var/log/vbox-install.log contain?

---

### Post by dramenard on 2009-03-04
Thank you marcelkoopman for your question,

/var/log/vbox-install.log is in the first post.

dramenard

---

### Post by marcelkoopman on 2009-03-05
Looks like the combination of VirtualBox 2.4.1 and this particular kernel doesnt work together.
Can you boot into a newer kernel? I think intrepid should have a new one.
Then do again:

```
sudo rm /usr/src/linux
```
```
sudo ln -s /usr/src/linux-header-xxxx /usr/src/linux
```

```
sudo /etc/init.d/vboxdrv setup
```

I think you should try a different kernel image.

---

