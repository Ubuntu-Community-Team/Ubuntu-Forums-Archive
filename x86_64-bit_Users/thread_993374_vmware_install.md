---
title: "vmware install"
date: 2008-11-25
forum: x86 64-bit Users
---

### Post by nkingcade on 2008-11-25
I attempted to install vmware on my x86_64 box. I received the following rejection:

neal@nealvinho:~/Desktop/vmware-server-distrib/installer$ sudo /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.27-7-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/pda.h:8,
                 from include/asm/current.h:19,
                 from include/asm/processor.h:15,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:12:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config1/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:71:
/tmp/vmware-config1/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config1/vmmon-only/linux/driver.c:146: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config1/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c:150: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config1/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1670: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.



Can someone enlighten me as to where I went wrong? Or point me to where I can research the problem? Thanks in advance.

---

### Post by Kilz on 2008-11-25
Where did you get the vmware install? What version is it?

---

### Post by bodhi.zazen on 2008-11-25
See the how-to I posted here :

[http://ubuntuforums.org/showthread.php?t=973756](http://ubuntuforums.org/showthread.php?t=973756)

Works for 64 bit, both 8.04 and 8.10 hosts.

---

### Post by madman100 on 2008-12-21
Hi nkingcade you need the lates version of vmware to be able to install it with out any problems 

Thanks
madman100

---

### Post by halavin on 2009-03-28
Please do this:

Go to System->Administration->Snaptic package manager and click it
type linux headers and install all the linux server , desktop and virtual machine headers for the version of kernel you are running, (uname -r).

download "vmware-any-any-update109" patch. Type that in google and you will come to the download link

tar xzf vmware-any-any-update109.gz and then run ./runme.pl

Hope this helps. It did for me. Good luck!

---

