---
title: "VMWare Workstation Feisty 64"
date: 2007-05-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by mburoff on 2007-05-25
**FIXED 24June07**

When installing VMWare Workstation 5.5 from command line it asks where the location of the C header files are.  I point it to the usual /usr/src/linux/include; however, I get the error 

> The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match 
your running kernel (version 2.6.20-15-generic).  Even if the module were to 
compile successfully, it would not load into the running kernel.


I went into /usr/src/linux/include/linux/version.h and added > #define UTS_RELEASE "2.6.20-15-generic"
 which is the kernel that I have.  Then when I try to install then I get this error:

> Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /usr/src/linux/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.c:80:
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;compat_exit&#8217;
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;exit_code&#8217;
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_syscall1&#8217;
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function &#8216;LinuxDriverNoPage&#8217;:
/tmp/vmware-config2/vmmon-only/linux/driver.c:1013: error: &#8216;mem_map&#8217; undeclared (first use in this function)
/tmp/vmware-config2/vmmon-only/linux/driver.c:1013: error: (Each undeclared identifier is reported only once
/tmp/vmware-config2/vmmon-only/linux/driver.c:1013: error: for each function it appears in.)
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function &#8216;LinuxDriverLockedNoPage&#8217;:
/tmp/vmware-config2/vmmon-only/linux/driver.c:1083: error: &#8216;mem_map&#8217; undeclared (first use in this function)
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.


I have no idea what's going wrong.  Any help would be greatly appreciated.  Thanks


Solution:  
In order to get VMWare working correctly I had to patch the vmmon file.  The patch is here:
[http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz)

When I came to the step of envoking /usr/bin/vmware-config.pl I entered no and then applied the patch.
VMWare then installed correctly.

---

### Post by jgrantham on 2007-06-01
I got VMWare Workstation 6 to install by doing one thing... 

Instead of editing the file loike you did, just go into your /usr/src folder and create a symbolic link using the following:

ln -s linux-headers-2.6.20-16-generic linux

Substitute the headers for your running kernel and it should work fine.

---

