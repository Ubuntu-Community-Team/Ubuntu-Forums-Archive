---
title: "VMwareTools-6.0.2-59824.tar.gz install error"
date: 2008-09-14
forum: x86 64-bit Users
---

### Post by endeavor2008 on 2008-09-14
Hi All,

My Ubuntu x86_64 (Linux MyDesktop 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux
) is running on VMware-6.0.2-59824, and I am trying to install VMwareTools-6.0.2-59824 using vmware-install.pl included in VMwareTools-6.0.2-59824.tar.gz.

It looks usr/bin/vmware-config-tools.pl  unable to build severl moudles, such as vmmemctl, vmhgfs , vmblock and vmci. 

Does anyone know how to solve this problem?

Many thanks for any response.

The error messages from vmware-config-tools.pl are listed as follows:
------------------------------------------------------------------
Before running VMware Tools for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config-tools.pl". Do you want 
this program to invoke the command for you now? [yes] 


Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:                                      done
Trying to find a suitable vmmemctl module for your running kernel.

None of the pre-built vmmemctl modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmmemctl module 
for your system (you need to have a C compiler installed on your system)? 
[yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-19-generic/build/include] 

Extracting the sources of the vmmemctl module.

Building the vmmemctl module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config14/vmmemctl-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config14/vmmemctl-only/os.o
In file included from /tmp/vmware-config14/vmmemctl-only/os.c:40:
/tmp/vmware-config14/vmmemctl-only/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config14/vmmemctl-only/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config14/vmmemctl-only/os.c:40:
/tmp/vmware-config14/vmmemctl-only/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
make[2]: *** [/tmp/vmware-config14/vmmemctl-only/os.o] Error 1
make[1]: *** [_module_/tmp/vmware-config14/vmmemctl-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vmmemctl.ko] Error 2
make: Leaving directory `/tmp/vmware-config14/vmmemctl-only'
Unable to build the vmmemctl module.

The memory manager driver (vmmemctl module) is used by VMware host software to 
efficiently reclaim memory from a virtual machine.
If the driver is not available, VMware host software may instead need to swap 
guest memory to disk, which may reduce performance.
The rest of the software provided by VMware Tools is designed to work 
independently of this feature.
If you want the memory management feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.
[ Press Enter key to continue ] 

Trying to find a suitable vmhgfs module for your running kernel.

None of the pre-built vmhgfs modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmhgfs module for
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vmhgfs module.

Building the vmhgfs module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config15/vmhgfs-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config15/vmhgfs-only/backdoor.o
  CC [M]  /tmp/vmware-config15/vmhgfs-only/backdoorGcc64.o
  CC [M]  /tmp/vmware-config15/vmhgfs-only/bdhandler.o
In file included from /tmp/vmware-config15/vmhgfs-only/dbllnklst.h:14,
                 from /tmp/vmware-config15/vmhgfs-only/vmrpc.h:17,
                 from /tmp/vmware-config15/vmhgfs-only/hgfsBd.h:14,
                 from /tmp/vmware-config15/vmhgfs-only/bdhandler.c:29:
/tmp/vmware-config15/vmhgfs-only/vm_basic_types.h:168: error: redefinition of typedef ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config15/vmhgfs-only/request.h:21,
                 from /tmp/vmware-config15/vmhgfs-only/bdhandler.c:34:
/tmp/vmware-config15/vmhgfs-only/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config15/vmhgfs-only/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config15/vmhgfs-only/request.h:21,
                 from /tmp/vmware-config15/vmhgfs-only/bdhandler.c:34:
/tmp/vmware-config15/vmhgfs-only/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
make[2]: *** [/tmp/vmware-config15/vmhgfs-only/bdhandler.o] Error 1
make[1]: *** [_module_/tmp/vmware-config15/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/vmware-config15/vmhgfs-only'
Unable to build the vmhgfs module.

The filesystem driver (vmhgfs module) is used only for the shared folder 
feature. The rest of the software provided by VMware Tools is designed to work 
independently of this feature.
If you wish to have the shared folders feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.
[ Press Enter key to continue ] 

Trying to find a suitable vmblock module for your running kernel.

None of the pre-built vmblock modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmblock module 
for your system (you need to have a C compiler installed on your system)? 
[yes] 

Extracting the sources of the vmblock module.

Building the vmblock module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config16/vmblock-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config16/vmblock-only/linux/block.o
In file included from /tmp/vmware-config16/vmblock-only/linux/os.h:21,
                 from /tmp/vmware-config16/vmblock-only/linux/block.c:12:
/tmp/vmware-config16/vmblock-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config16/vmblock-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config16/vmblock-only/linux/os.h:21,
                 from /tmp/vmware-config16/vmblock-only/linux/block.c:12:
/tmp/vmware-config16/vmblock-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config16/vmblock-only/linux/vmblockInt.h:26,
                 from /tmp/vmware-config16/vmblock-only/linux/block.c:15:
/tmp/vmware-config16/vmblock-only/./include/vm_basic_types.h:168: error: redefinition of typedef ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/tmp/vmware-config16/vmblock-only/linux/block.o] Error 1
make[1]: *** [_module_/tmp/vmware-config16/vmblock-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vmblock.ko] Error 2
make: Leaving directory `/tmp/vmware-config16/vmblock-only'
Unable to build the vmblock module.

The vmblock module enables dragging or copying files from within a host and 
dropping or pasting them onto your guest (host to guest drag and drop and file 
copy/paste).  The rest of the software provided by VMware Tools is designed to 
work independently of this feature (including guest to host drag and drop and 
file copy/paste).

If you would like the host to guest drag and drop and file copy/paste features,
you can install the driver by running vmware-config-tools.pl again after making
sure that gcc, binutils, make and the kernel sources for your running kernel 
are installed on your machine. These packages are available on your 
distribution's installation CD.
[ Press Enter key to continue ] 

[EXPERIMENTAL] The Virtual Machine Communication Interface (VMCI) service 
provides a new communication capability with the Host, primarily for 
development at the moment.  Would you like to enable this feature? [yes] 

Trying to find a suitable vmci module for your running kernel.

None of the pre-built vmci modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmci module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vmci module.

Building the vmci module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config17/vmci-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config17/vmci-only/dbllnklst.o
  CC [M]  /tmp/vmware-config17/vmci-only/kernelStubsLinux.o
In file included from include/linux/kernel.h:13,
                 from /tmp/vmware-config17/vmci-only/kernelStubs.h:19,
                 from /tmp/vmware-config17/vmci-only/kernelStubsLinux.c:14:
include/linux/types.h:40: error: redefinition of typedef ‘uintptr_t’
/tmp/vmware-config17/vmci-only/vm_basic_types.h:168: error: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/tmp/vmware-config17/vmci-only/kernelStubsLinux.o] Error 1
make[1]: *** [_module_/tmp/vmware-config17/vmci-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vmci.ko] Error 2
make: Leaving directory `/tmp/vmware-config17/vmci-only'
Unable to build the vmci module.

The communication service is used in addition to the standard communication 
between the guest and the host.  The rest of the software provided by VMware 
Tools is designed to work independently of this feature.
If you wish to have the VMCI feature, you can install the driver by running 
vmware-config-tools.pl again after making sure that gcc, binutils, make and the
kernel sources for your running kernel are installed on your machine. These 
packages are available on your distribution's installation CD.
[ Press Enter key to continue ] 



Detected X.org version 0.0.0.



No drivers for X.org version: 0.0.0.



Do you want to change the display size that X starts with? (yes/no) [no] 

Starting VMware Tools services in the virtual machine:
   Switching to guest configuration:                                   done
   DMA setup:                                                          done
   Guest operating system daemon:                                      done

The configuration of VMware Tools 6.0.2 build-59824 for Linux for this running 
kernel completed successfully.

You must restart your X session before any mouse or graphics changes take 
effect.

You can now run VMware Tools by invoking the following command: 
"/usr/bin/vmware-toolbox" during an X server session.

To make use of the virtual printer, you will need to restart the CUPS service

Enjoy,

--the VMware team
------------------------------------------------------------------

---

