---
title: "Vmware install problem..."
date: 2005-11-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by dbee on 2005-11-24
I can't seem to install vmware on my AMD64 ubuntu ...
All I get is this error from the perl install file 
```

 Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.12-9-amd64-generic/build/include/.. SUBDIRS=$PWD SRCROO T=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-amd64-generic'
CC [M] /tmp/vmware-config0/vmmon-only/linux/driver.o
/tmp/vmware-config0/vmmon-only/linux/driver.c:33:25: asm/ioctl32.h: No such file or directory
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function `register_ioctl32_han dlers':
/tmp/vmware-config0/vmmon-only/linux/driver.c:222: warning: implicit declaration of function `register_ioctl32_conversion'
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function `unregister_ioctl32_h andlers':
/tmp/vmware-config0/vmmon-only/linux/driver.c:248: warning: implicit declaration of function `unregister_ioctl32_conversion'
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-amd64-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

I found this solution on the net - but it's for SUSE
```

cd /usr/src/linux 
make cloneconfig 
make modules_prepare 
/usr/bin/vmware-config.pl

```

... Is this a 64bit issue with vmware ?? ... I have a /usr/src file on my system but there isn't any make files in it - there's just some kernel header files.

---

### Post by Hallavej on 2005-11-25
Download the latest any-any-update, untar it and run the runme.pl file
[ftp://platan.vc.cvut.cz/pub/vmware/](ftp://platan.vc.cvut.cz/pub/vmware/)

---

### Post by X3N on 2005-11-25
This solved the problem for me as well..

After exporting the CC version; export CC=/usr/bin/gcc-3.4

which solves this error:

"Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware
Workstation cannot work in such configuration. Please either recompile your
kernel with "/usr/bin/gcc" version "4.0.2", or restart /usr/bin/vmware-config.plwith CC environment variable pointing to the "gcc" version "3.4.5".

---

