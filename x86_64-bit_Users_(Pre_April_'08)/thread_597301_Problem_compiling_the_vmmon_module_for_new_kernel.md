---
title: "Problem compiling the vmmon module for new kernel"
date: 2007-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2007-10-30
chris@ubuntu:~/Desktop$ sudo /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.23.1custom1/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.23.1custom1/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-2.6.23.1'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function `LinuxDriver_Ioctl':
/tmp/vmware-config2/vmmon-only/linux/driver.c:1659: error: structure has no member named `dumpable'
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.23.1'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

chris@ubuntu:~/Desktop$

---

