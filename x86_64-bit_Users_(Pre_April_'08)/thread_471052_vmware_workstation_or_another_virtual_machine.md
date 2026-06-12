---
title: "vmware workstation or another virtual machine"
date: 2007-06-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Iron64 on 2007-06-11
Hello, my problem is:

I want to install vmware workstation, and this is the error message:

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:80:
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

In alternative i can install another virtual machine, which is the most easy?

thank you for all answer

---

### Post by tgm4883 on 2007-06-11
Hmm, well you could install Virtualbox which now has AMD64 support.  (although you cant as of yet install 64-bit guest OS's)  It's pretty easy to use.

You already spent the $189 on VMware Workstation.  I would try to get that working first.  Of course thats just me not liking to waste $189

---

### Post by capecove on 2007-06-11
I agree completely with the above post. I got Virtualbox running without any problems at all. But, I would just about die knowing I had already spent the $189. So, getting that going is likely your first priority.

---

### Post by capecove on 2007-06-12
Hey Iron64.... A quick search of the forums here found this...

[http://ubuntuforums.org/showthread.php?t=283454](http://ubuntuforums.org/showthread.php?t=283454)

Check it out, it may help you out some. Let us know how it works out for you...

---

