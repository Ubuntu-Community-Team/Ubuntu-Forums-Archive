---
title: "Can't install vmware server 2 on 64 bit ubuntu"
date: 2009-03-23
forum: x86 64-bit Users
---

### Post by styleruk on 2009-03-23
Hi, I have just changed from 32 bit to 64 bit Ubuntu and found that he install for server 2 does not complete. See below for the output. It mentions that I have a 'module -related problem'. Can anyone help?

I'm using Ubuntu 8.10 64 bit and the latest vmware server 2.

Regards

Si

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.27-11-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
CC [M] /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/./include/machine.h:24,
from /tmp/vmware-config2/vmmon-only/linux/driver.h:15,
from /tmp/vmware-config2/vmmon-only/linux/driver.c:49:
/tmp/vmware-config2/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/pda.h:8,
from include/asm/current.h:19,
from include/asm/processor.h:15,
from include/linux/prefetch.h:14,
from include/linux/list.h:6,
from include/linux/module.h:9,
from /tmp/vmware-config2/vmmon-only/linux/driver.c:12:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config2/vmmon-only/linux/vmhost.h:13,
from /tmp/vmware-config2/vmmon-only/linux/driver.c:71:
/tmp/vmware-config2/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config2/vmmon-only/linux/driver.c:146: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config2/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c:150: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config2/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config2/vmmon-only/linux/driver.c:1670: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** _module_/tmp/vmware-config2/vmmon-only Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [http://vmmon.ko](http://vmmon.ko) Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

simon@simon-desktop:~$

---

### Post by ubersolid on 2009-03-23
Do you have the build tools installed?
build-essential and kernel-package is needed to build the modules.
I have vmware-server 2 installed in 64-bit ubuntu 8.10 myself, it installed without any problems.

just ```
sudo aptitude install build-essential kernel-package
``` and you'll be fine.

---

### Post by styleruk on 2009-03-23
I have;
dpkg-dev
build-essential

but I can't find just 'build tools' in the package manager anywhere.

Si

---

### Post by styleruk on 2009-03-23
I don't believe it!  I found the problem...I was trying to install vmware server 1 and not 2!  I must have downloaded the wrong one.

Thanks for your reply, it was quick.  I had this posted on the vmware newsgroups for days with no reply.

---

### Post by ubersolid on 2009-03-23
by "build tools" I meant build-essential and kernel-package, glad you figured it out! :)

---

### Post by styleruk on 2009-03-23
I still have a prolbem though, It's something to do with firefox as firefox has gone very strange.  The back button does not work for instance, foxmarks does not work in fact anything that you click on does not work correctly, no home page etc...

When vmware tries to fire up it comes up with initializing monitor error....

Is there a way to make vmware use a different browser or is there a real way of completely re-installing firefox?

Si

---

### Post by styleruk on 2009-03-23
AHHH!  Have it...Sorry to blab on like this but if anyone else searches for what I've found then it may help them.

Firstly, not sure what I did to screw firefox but I found that if I deleted the local user config files then it works fine again.  Found out by setting up another login and firefox worked fine.

Then...
Vmware, found out that I had KVM running...

[http://communities.vmware.com/thread/157648](http://communities.vmware.com/thread/157648)

So uninstalled this and voila, the vm was able to open in it's own monitor.  Now I can get back to work, although, I prefer to tinker with Ubuntu than work...never mind.

Thanks for you help anyway

Si

---

