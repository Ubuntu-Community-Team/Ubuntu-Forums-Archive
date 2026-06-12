---
title: "Compiling vmware server 1.04/1.05 vmmon module errors on 8.04 64bit"
date: 2008-04-25
forum: x86 64-bit Users
---

### Post by archlich on 2008-04-25
I googled for a fix and didn't find anything of use.

Has anyone else seen this?

```

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config3/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:48:
/tmp/vmware-config3/vmmon-only/./include/vm_basic_types.h:159: error: redefinition of typedef ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config3/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:49:
/tmp/vmware-config3/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config3/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config3/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:49:
/tmp/vmware-config3/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config3/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config3/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config3/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config3/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config3/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```

In the meanwhile, I'll keep searching for a workaround.

---

### Post by Breneez on 2008-04-25
I have the same problem on 8.04 32-bit

---

### Post by viper8 on 2008-04-26
I had this same issue and, as always, the best fix is to run the vmware-any-any patch available at (the latest is 115):

[http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update115.tar.gz](http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update115.tar.gz)

1) Run the vmware install like normal
2) tar xvfz the file you downloaded above
3) run ./runme.pl from the vmware-any-any directory and it will patch the necessary vmware related files and compile the modules.

Let me know if you need any help.

--
Dave

---

### Post by snafilter on 2008-04-26
After installing the any any patch, I ran into some additional problems.  They were resloved by the following post, (in case you have them as well)
[URL="http://ubuntuforums.org/showthread.php?t=337040"]
http://ubuntuforums.org/showthread.php?t=337040[/URL]

---

### Post by darknight2183 on 2008-04-27
viper8,
  I applied the any-any patch, much like one had to do when Feisty first came out, but I'm still receiving errors when compiling. Check it out below:

In file included from include/asm/bitops.h:2,
                 from /tmp/vmware-config5/vmmon-only/./include/vcpuset.h:74,
                 from /tmp/vmware-config5/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config5/vmmon-only/common/vmx86.h:19,
                 from /tmp/vmware-config5/vmmon-only/common/hostif.h:18,
                 from /tmp/vmware-config5/vmmon-only/common/cpuid.c:15:
include/asm/bitops_32.h:9:2: error: #error only <linux/bitops.h> can be included directly
make[2]: *** [/tmp/vmware-config5/vmmon-only/common/cpuid.o] Error 1
make[1]: *** [_module_/tmp/vmware-config5/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config5/vmmon-only'
Unable to build the vmmon module.

Near as I can tell, there are no problems with my dependances, or with my libs.  Yet somehow I seem to be missing that d*mn boolen code needed.  Any idea's?

---

### Post by archlich on 2008-04-30
There's a few c libraries not included with build essential so installing g++ solves that.

```
sudo apt-get install g++
```

Grab the patch from here so the kernel modules compile correctly.

[http://howtoforge.com/vmware-server-1.0.4-fedora8-kernel-2.6.24](http://howtoforge.com/vmware-server-1.0.4-fedora8-kernel-2.6.24)

```
tar xvfj vmware.tar.bz2
cd vmware/
cp vm* /usr/lib/vmware/modules/source/
```

alternatively since this is a first install, copy them over to the vmware-server-distrib/lib/vmware/module/source directory 

Stopped with this error:

```
Unable to make the Internet super-server (inetd) re-read its configuration 
```
Just hit enter

If you try to run the console ($vmware)you'll get a bunch of errors stating:

```
/usr/lib/vmware/bin/vmware: libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

```

There's an error with the older ia32-libs so run this to copy the newer libs over vmwares older ones

```
sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
```

The icons aren't pretty, but it works.


Here's the links I used that helped me through this process:
[http://howtoforge.com/vmware-server-1.0.4-fedora8-kernel-2.6.24](http://howtoforge.com/vmware-server-1.0.4-fedora8-kernel-2.6.24)
[http://ubuntuforums.org/showthread.php?t=772757](http://ubuntuforums.org/showthread.php?t=772757)
[http://x86virtualization.com/virtualizationnews/howto-run-vmware-server-console-105-in-ubuntu-hardy-804.html](http://x86virtualization.com/virtualizationnews/howto-run-vmware-server-console-105-in-ubuntu-hardy-804.html)

---

### Post by Kilz on 2008-04-30
:)

---

### Post by andrewisett on 2008-05-01
> **archlich said:**
> ...The icons aren't pretty, but it works...


Here's the links I used that helped me through this process:
[http://howtoforge.com/vmware-server-1.0.4-fedora8-kernel-2.6.24](http://howtoforge.com/vmware-server-1.0.4-fedora8-kernel-2.6.24)
[http://ubuntuforums.org/showthread.php?t=772757](http://ubuntuforums.org/showthread.php?t=772757)
[http://x86virtualization.com/virtualizationnews/howto-run-vmware-server-console-105-in-ubuntu-hardy-804.html](http://x86virtualization.com/virtualizationnews/howto-run-vmware-server-console-105-in-ubuntu-hardy-804.html)

Any one discovered how to point to the 'normal' icons?  I need to be able to tell at a glance whether the 10 machines I have are powered on, and the green arrow is gone.

Here's the actual error message:

Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

I could be completely wrong here - but if you look at /usr/l3232 <-- is not an actual directory unless that is pointing to a shortcut?  In the /usr/l32/gtk-2.0/2.10./loaders/ there is the file that the line references, so maybe there is a way to just edit that line to point to the correct location?

---

### Post by Nathan_Rollins on 2008-05-01
> **andrewisett said:**
> Any one discovered how to point to the 'normal' icons?  I need to be able to tell at a glance whether the 10 machines I have are powered on, and the green arrow is gone.

Here's the actual error message:

Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

I could be completely wrong here - but if you look at /usr/l3232 <-- is not an actual directory unless that is pointing to a shortcut?  In the /usr/l32/gtk-2.0/2.10./loaders/ there is the file that the line references, so maybe there is a way to just edit that line to point to the correct location?

This isn't a "fix" per se, but I just created a symlink for the /usr/l3232 the Vmware console was looking for:

```
sudo ln -s /usr/lib32 /usr/l3232
```

Now the console runs correctly.  Looks like there is a typo in the console code, but that is for an "expert" to figure out. :)

---

### Post by amorangi on 2008-05-07
Just the fix I was looking for!

---

