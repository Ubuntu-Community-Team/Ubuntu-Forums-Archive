---
title: "vmware5 not installing using dapper"
date: 2006-09-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by madubuntuer on 2006-09-20
Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.15-23-amd64-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-amd64-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
/tmp/vmware-config2/vmmon-only/linux/driver.c:33:25: error: asm/ioctl32.h: No such file or directory
In file included from /tmp/vmware-config2/vmmon-only/./include/vmware.h:24,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:44:
/tmp/vmware-config2/vmmon-only/./include/vm_basic_defs.h:208:5: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config2/vmmon-only/./include/vcpuset.h:56,
                 from /tmp/vmware-config2/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config2/vmmon-only/./common/vmx86.h:18,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:45:
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:54:5: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config2/vmmon-only/./include/vm_asm.h:23,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:48:
/tmp/vmware-config2/vmmon-only/./include/vm_basic_asm.h:48:5: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function ‘register_ioctl32_handlers’:
/tmp/vmware-config2/vmmon-only/linux/driver.c:222: warning: implicit declaration of function ‘register_ioctl32_conversion’
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function ‘unregister_ioctl32_handlers’:
/tmp/vmware-config2/vmmon-only/linux/driver.c:248: warning: implicit declaration of function ‘unregister_ioctl32_conversion’
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-amd64-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

---

### Post by mitch.c on 2006-09-20
> **madubuntuer said:**
> 
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-amd64-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
/tmp/vmware-config2/vmmon-only/linux/driver.c:33:25: error: asm/ioctl32.h: No such file or directory
...
Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-amd64-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

It looks to me like you don't have the proper kernel headers loaded. A package search on asm/ioctl32.h doesn't come up in linux-headers-2.6.15-23-amd64-generic. Are you sure you can build this on amd64?

EDIT: I do see ioctl32.h is part of linux-headers-2.6.15-22-k7.

---

