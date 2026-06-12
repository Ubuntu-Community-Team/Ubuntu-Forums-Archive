---
title: "VMware Server down"
date: 2007-01-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Doug11 on 2007-01-19
I'm running Edgy64 and I just compiled to the the 2.6.19 Kernel. Everything went as planned,, I still have my wireless, a good diference in speed, but somewhere along the line I thought I seen that I would have to do something with my VMware to get it running again. I looked around again but could not find the post. Like they said, it will not start. Does anyone know what I have to do to get it running agian?

---

### Post by DerHesse on 2007-01-19
uninstall and install, since it seems you have a newer kernel version than at the time you first installed vmware.:rolleyes:

i did it severel times allready, if there is another way i'd bee interested , too.

---

### Post by enopepsoo on 2007-01-19
you can just run the vmware-config.pl file.  It will redo the part where it compiles whatever to match your kernel.

all the default settings should still apply. :cool:

---

### Post by Doug11 on 2007-01-19
Sorry for my ignorance but,,where might i find that and how?

---

### Post by Doug11 on 2007-01-20
ok,,i tried to uninstall and reinstall and come into this error>>>>

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmnet-only'
make -C /lib/modules/2.6.19.1/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-2.6.19'
  CC [M]  /tmp/vmware-config1/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config1/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config1/vmnet-only/userif.o
/tmp/vmware-config1/vmnet-only/userif.c: In function ‘VNetCopyDatagramToUser’:
/tmp/vmware-config1/vmnet-only/userif.c:629: error: ‘CHECKSUM_HW’ undeclared (first use in this function)
/tmp/vmware-config1/vmnet-only/userif.c:629: error: (Each undeclared identifier is reported only once
/tmp/vmware-config1/vmnet-only/userif.c:629: error: for each function it appears in.)
make[2]: *** [/tmp/vmware-config1/vmnet-only/userif.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.19'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

Could this have something to do with an incomplete uninstall?

---

### Post by Hershey on 2007-01-20
See if this helps with the vmnet issue:

[http://www.ubuntuforums.org/showthread.php?t=334394](http://www.ubuntuforums.org/showthread.php?t=334394)

---

### Post by Doug11 on 2007-01-23
> **Hershey said:**
> See if this helps with the vmnet issue:

[http://www.ubuntuforums.org/showthread.php?t=334394](http://www.ubuntuforums.org/showthread.php?t=334394)


Thanks Hershey,,,that did the trick.

---

