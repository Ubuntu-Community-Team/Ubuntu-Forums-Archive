---
title: "wireless usb-dongle amd64 problem"
date: 2006-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by kedde on 2006-09-11
I have installed ubuntu-x64 and I'm trying to get my wireless USB-dongle(D-link dwl-g122) to work.

I followed this thread: [http://ubuntuforums.org/showthread.php?t=190422&page=2&highlight=dwl+g122]("http://ubuntuforums.org/showthread.php?t=190422&page=2&highlight=dwl+g122")

but when i run the command "make all" i get the following error:
```

root@keddeDesktop:/home/kedde/RT73_Linux_STA_Drv1.0.3.6/Module# make all
make -C /lib/modules/2.6.15-26-amd64-generic/build SUBDIRS=/home/kedde/RT73_Linux_STA_Drv1.0.3.6/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-amd64-generic'
  CC [M]  /home/kedde/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o
In file included from /home/kedde/RT73_Linux_STA_Drv1.0.3.6/Module/rt_config.h:99,
                 from /home/kedde/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:40:
include/asm-i386/atomic.h:19: error: conflicting types for ‘atomic_t’
include/asm/atomic.h:18: error: previous declaration of ‘atomic_t’ was here
include/asm-i386/atomic.h:48: error: conflicting types for ‘atomic_add’
include/asm/atomic.h:47: error: previous definition of ‘atomic_add’ was here
include/asm-i386/atomic.h:63: error: conflicting types for ‘atomic_sub’
include/asm/atomic.h:62: error: previous definition of ‘atomic_sub’ was here
include/asm-i386/atomic.h:80: error: conflicting types for ‘atomic_sub_and_test’
include/asm/atomic.h:79: error: previous definition of ‘atomic_sub_and_test’ was here
include/asm-i386/atomic.h:97: error: conflicting types for ‘atomic_inc’
include/asm/atomic.h:96: error: previous definition of ‘atomic_inc’ was here
include/asm-i386/atomic.h:111: error: conflicting types for ‘atomic_dec’
include/asm/atomic.h:110: error: previous definition of ‘atomic_dec’ was here
include/asm-i386/atomic.h:127: error: conflicting types for ‘atomic_dec_and_test’
include/asm/atomic.h:126: error: previous definition of ‘atomic_dec_and_test’ was here
include/asm-i386/atomic.h:146: error: conflicting types for ‘atomic_inc_and_test’
include/asm/atomic.h:145: error: previous definition of ‘atomic_inc_and_test’ was here
include/asm-i386/atomic.h:166: error: conflicting types for ‘atomic_add_negative’
include/asm/atomic.h:165: error: previous definition of ‘atomic_add_negative’ was here
include/asm-i386/atomic.h:184: error: conflicting types for ‘atomic_add_return’
include/asm/atomic.h:183: error: previous definition of ‘atomic_add_return’ was here
include/asm-i386/atomic.h:209: error: conflicting types for ‘atomic_sub_return’
include/asm/atomic.h:193: error: previous definition of ‘atomic_sub_return’ was here
In file included from /home/kedde/RT73_Linux_STA_Drv1.0.3.6/Module/rt_config.h:99,
                 from /home/kedde/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:40:
include/asm-i386/atomic.h:242:1: warning: "atomic_set_mask" redefined
In file included from include/asm/spinlock.h:4,
                 from include/linux/spinlock.h:88,
                 from include/linux/capability.h:45,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/kedde/RT73_Linux_STA_Drv1.0.3.6/Module/rt_config.h:63,
                 from /home/kedde/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:40:
include/asm/atomic.h:411:1: warning: this is the location of the previous definition
/home/kedde/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c: In function ‘usb_rtusb_probe’:
/home/kedde/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2085: warning: unused variable ‘device’
make[2]: *** [/home/kedde/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/kedde/RT73_Linux_STA_Drv1.0.3.6/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-amd64-generic'
make: *** [all] Error 2


```

Any suggestions?

---

